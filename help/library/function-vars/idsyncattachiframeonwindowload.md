---
description: Un indicador booleano opcional que controla cómo carga el servicio de Experience Cloud ID el iFrame de sincronización de ID.
keywords: Servicio de ID
title: idSyncAttachIframeOnWindowLoad
exl-id: 44c45378-f007-4d87-913a-d6bb9961948c
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '77'
ht-degree: 100%

---

# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

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
