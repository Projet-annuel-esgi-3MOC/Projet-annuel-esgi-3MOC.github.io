---
title: "CDN Firabase Storage"
date: 2023-08-25T01:41:43+02:00
draft: false
---

On a du changer les regles de notre storage ainsi


```
rules_version = '2';
service firebase.storage {
  match /b/{bucket}/o {
    match /{allPaths=**} {
      allow read: if request.origin == "*";
    }
  }
}
```

depuis

```
rules_version = '2';
service firebase.storage {
  match /b/{bucket}/o {
    match /{allPaths=**} {
      allow read, write: if false;
    }
  }
}
```