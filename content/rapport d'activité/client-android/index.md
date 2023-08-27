---
title: "Client Android"
date: 2023-08-26T00:08:35+02:00
draft: false
---

Pour le splashscreen

https://shapeshifter.design

https://developer.android.com/reference/kotlin/androidx/core/splashscreen/SplashScreen

https://developer.android.com/develop/ui/views/launch/splash-screen

Impossible de faire des appel sur http://localhost:3000 car depuis une certaine version android bloque les appel reseau non protegés par https.

`java.net.UnknownServiceException: CLEARTEXT communication to localhost not permitted by network security policy`

La solution est de creer un fichier
network_security_config.xml et d'y mettre

```xml
<network-security-config>
    <domain-config cleartextTrafficPermitted="true">
        <domain includeSubdomains="true">localhost</domain>
    </domain-config>
</network-security-config>

```

Ensuite au lieu de taper sur localhost ou `10.0.2.2`, il faut taper sur l'hote de la machine cible dans le reseau local, hote trouvable via `ifconfig`. l'interface a trouver est `en0`. il faut aussi l'ajouter dans les exceptions xml

Il faut aussi faire du port forwarding

```
adb forward tcp:3000 tcp:3000
```

Mais avant ajouter adb dans le path, dans .zshrc

```
export PATH="$PATH":"$HOME/Library/Android/sdk/platform-tools/"
```

Pour la deserialization on doit utiliser des type adapters, eg

```kotlin
import com.google.gson.annotations.JsonAdapter
import com.google.gson.Gson
import java.lang.reflect.Type
import java.text.SimpleDateFormat
import java.util.*

data class Person(val name: String, @JsonAdapter(DateTypeAdapter::class) val birthInfo: BirthInfo)

data class BirthInfo(val birthDate: Date)

class DateTypeAdapter : JsonSerializer<Date>, JsonDeserializer<Date> {
    private val dateFormat = SimpleDateFormat("yyyy-MM-dd", Locale.getDefault())

    override fun serialize(src: Date?, typeOfSrc: Type?, context: JsonSerializationContext?): JsonElement {
        return JsonPrimitive(dateFormat.format(src))
    }

    override fun deserialize(json: JsonElement?, typeOfT: Type?, context: JsonDeserializationContext?): Date {
        val dateStr = json?.asString
        return dateFormat.parse(dateStr)
    }
}

fun main() {
    val gson = Gson()

    val birthInfo = BirthInfo(Date())
    val person = Person("John Doe", birthInfo)
    val json = gson.toJson(person)
    println(json)

    val jsonPerson = """{"name":"Jane Smith","birthInfo":{"birthDate":"2023-08-27"}}"""
    val deserializedPerson = gson.fromJson(jsonPerson, Person::class.java)
    println(deserializedPerson)
}

```

Finalement utiliser retrofit est trop compliqué car il ignore les anotation
@JsonAdapter https://stackoverflow.com/questions/52434317/does-gson-ignore-jsonadapter-on-jsonelement-fields

On utilisera Volley comme dans notre projet android spotify

Pour que le fragment container n'empiete pas sur le navgraph, il faut lui donner une hauteur de 0 et la contraindre au top du navbar, si on contraint le top du navbar au bottom du fragment, le navbar est poussé vers le bas