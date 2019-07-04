---
description: Un indicador booleano opcional que deshabilita la sincronización de los ID.
keywords: Servicio de ID
seo-description: Un indicador booleano opcional que deshabilita la sincronización de los ID.
seo-title: disableIdSyncs
title: disableIdSyncs
uuid: 8bea1de8-53c8-4a15-bcf5-f0869763a32e
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

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

