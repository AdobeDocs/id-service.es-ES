---
description: Un indicador booleano opcional que deshabilita la sincronización de los ID.
keywords: Servicio de ID
seo-description: Un indicador booleano opcional que deshabilita la sincronización de los ID.
seo-title: disableIdSyncs
title: disableIdSyncs
uuid: 8 bea 1 de 8-53 c 8-4 a 15-bcf 5-f 0869763 a 32 e
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# disableIdSyncs{#disableidsyncs}

Un indicador booleano opcional que deshabilita la sincronización de los ID.

>[!NOTE]
>
>Esta configuración se ha cambiado `idSyncDisableSyncs` de nombre `disableIdSyncs` en la versión del 18 de enero de 2018 de la versión v 3.0.

**Sintaxis:**`disableIdSyncs: true|false` (el valor predeterminado `false`es.)

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

