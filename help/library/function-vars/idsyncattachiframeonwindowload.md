---
description: Un indicador booleano opcional que controla cómo carga el servicio de ID de visitante el iFrame de sincronización de ID.
keywords: Servicio de ID de visitante
title: idSyncAttachIframeOnWindowLoad
exl-id: 44c45378-f007-4d87-913a-d6bb9961948c
TQID: https://experienceleague.adobe.com/fEqtHlUaNadgatKX-V-7FuZn-WTZOFg-YtBOD7yKg0k
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 78
ht-degree: 16%

---

# idSyncAttachIframeOnWindowLoad{#idsyncattachiframeonwindowload}

Un indicador booleano opcional que controla cómo carga el servicio de ID de visitante el iFrame de sincronización de ID.

**Sintaxis:** ` `idSyncAttachIframeOnWindowLoad= true false`` (el valor predeterminado es `false`).

Cuando `idSyncAttachIframeOnWindowLoad: true`, el servicio de ID de visitante carga el iFrame de sincronización de ID en la ventana de carga. De forma predeterminada, el servicio de ID de visitante carga el iFrame de sincronización con el ID lo más rápido posible en lugar de al cargar la ventana.

**Ejemplo de código**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example loads ID sync iFrame on window load instad of ASAP. 
   idSyncAttachIframeOnWindowLoad: true 
});
```

