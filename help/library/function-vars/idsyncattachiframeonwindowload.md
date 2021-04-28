---
description: Un indicador booleano opcional que controla cómo carga el servicio de Experience Cloud ID el iFrame de sincronización de ID.
keywords: Servicio de ID
seo-description: Un indicador booleano opcional que controla cómo carga el servicio de Experience Cloud ID el iFrame de sincronización de ID.
seo-title: idSyncAttachIframeOnWindowLoad
title: idSyncAttachIframeOnWindowLoad
uuid: aa2c2fa4-2cab-4e08-8d35-729a6c3e459a
exl-id: 44c45378-f007-4d87-913a-d6bb9961948c
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '95'
ht-degree: 100%

---

# idSyncAttachIframeOnWindowLoad {#idsyncattachiframeonwindowload}

Un indicador booleano opcional que controla cómo carga el servicio de Experience Cloud ID el iFrame de sincronización de ID.

**Sintaxis:** ` `idSyncAttachIframeOnWindowLoad= true false`` (el valor predeterminado es `false`).

Cuando `idSyncAttachIframeOnWindowLoad: true`, el servicio de ID carga la sincronización iFrame de ID en la ventana de carga. De forma predeterminada, el servicio de ID carga el iFrame de sincronización con el ID lo más rápido posible en lugar de al cargar la ventana.

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
