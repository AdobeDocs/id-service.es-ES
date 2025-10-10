---
description: Esta variable le permite sobrescribir el intervalo de duración predeterminado para la cookie de AMCV.
keywords: Servicio de ID
title: cookieLifetime
exl-id: bdbabdcd-a87b-412c-8c2f-3f39820f939a
source-git-commit: 7ef084bc1add5a4ea8c7be738055b0c21e247eea
workflow-type: tm+mt
source-wordcount: '50'
ht-degree: 100%

---

# cookieLifetime{#cookielifetime}

Esta variable le permite sobrescribir el intervalo de duración predeterminado para la cookie de AMCV.

De manera predeterminada, las cookies del servicio de [!DNL Experience Cloud] ID de caducan tras 24 meses. Establezca el intervalo de tiempo en segundos.

**Sintaxis:** `cookieLifetime: *`duración en segundos`*`

**Ejemplo de código**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable. Example changes expiration period to 12-months. 
   cookieLifetime:31536000 
});
```
