---
description: Un indicador booleano opcional que deshabilita la sincronización de los ID.
keywords: Servicio de ID
title: disableIdSyncs
exl-id: 96d42133-6040-4da3-9315-fd94318b33aa
source-git-commit: e185c7d2b7582b52adbe9b525be7868ab8bfa374
workflow-type: tm+mt
source-wordcount: '37'
ht-degree: 100%

---

# disableIdSyncs{#disableidsyncs}

Un indicador booleano opcional que deshabilita la sincronización de los ID.

>[!NOTE]
>
>Esta configuración era `idSyncDisableSyncs` y pasó a denominarse `disableIdSyncs` en la versión 3.0 del 18 de enero de 2018.

**Sintaxis:** `disableIdSyncs: true|false` (el valor predeterminado es `false`)

**Ejemplo de código**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableIdSyncs: true 
});
```

