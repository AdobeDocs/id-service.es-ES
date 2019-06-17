---
description: Un indicador booleano opcional que controla cómo carga el servicio Experience Cloud ID el iFrame de sincronización de ID.
keywords: Servicio de ID
seo-description: Un indicador booleano opcional que controla cómo carga el servicio Experience Cloud ID el iFrame de sincronización de ID.
seo-title: idSyncAttachIframeOnWindowLoad
title: idSyncAttachIframeOnWindowLoad
uuid: aa 2 c 2 fa 4-2 cab -4 e 08-8 d 35-729 a 6 c 3 e 459 a
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

Un indicador booleano opcional que controla cómo carga el servicio Experience Cloud ID el iFrame de sincronización de ID.

**Sintaxis:**` `Idsyncattachiframeonwindowload = true | false &quot; (predeterminado es `false`&quot;.

Cuando `idSyncAttachIframeOnWindowLoad: true`, el servicio de ID carga la sincronización iFrame de ID en la ventana de carga. De forma predeterminada, el servicio de ID carga el iFrame de sincronización de ID lo más rápido posible, en lugar de cuando se carga la ventana.

**Ejemplo de código**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example loads ID sync iFrame on window load instad of ASAP. 
   idSyncAttachIframeOnWindowLoad: true 
});
```

