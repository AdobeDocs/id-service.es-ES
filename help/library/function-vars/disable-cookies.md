---
description: Un indicador booleano opcional que evita que el servicio de ID de visitante devuelva la cookie de terceros demdex.net.
keywords: Servicio de ID de visitante
title: disableThirdPartyCookies
exl-id: 19d12822-0e17-4a1c-8e9c-25a22e20a4a8
TQID: https://experienceleague.adobe.com/vx9q-Q1X0fraWPUmaBlx-bBFX-gvnAox03mpENTizHw
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 144
ht-degree: 16%

---

# disableThirdPartyCookies{#disablethirdpartycookies}

Un indicador booleano opcional que evita que el servicio de ID de visitante devuelva la cookie de terceros demdex.net.

>[!NOTE]
>
>Esta configuración era `idSyncDisable3rdPartySyncing` y pasó a denominarse `disableThirdPartyCookies` en la versión 3.0 del 18 de enero de 2018.

**Sintaxis:** `disableThirdPartyCookies: true|false` (el valor predeterminado es `false`) Para `VisitorAPI.js` v3.0.0 o posterior.

Cuando `disableThirdPartyCookies: true`, el servicio de identificación del visitante no devuelve la cookie demdex.net de terceros (consulte [Cookies y el servicio de identificación del visitante](../../introduction/cookies.md) ). Si el visitante de un sitio tiene ya esta cookie en su explorador, el servicio de ID de visitante no la usará para crear un nuevo ECID o devolver un ID existente. En su lugar, el servicio de ID de visitante crea un MID aleatorio nuevo en la cookie de origen. Una vez activado, puede recopilar datos con el servicio de ID de visitante y compartirlos en diferentes soluciones de CX Enterprise.

**Ejemplo de código**

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCookies: true 
});
```

