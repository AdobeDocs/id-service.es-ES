---
description: Un indicador booleano opcional que evita que el servicio de identidad de Experience Cloud devuelva la cookie de terceros demdex.net.
keywords: Servicio de ID
title: disableThirdPartyCookies
exl-id: 19d12822-0e17-4a1c-8e9c-25a22e20a4a8
TQID: https://experienceleague.adobe.com/vx9q-Q1X0fraWPUmaBlx-bBFX-gvnAox03mpENTizHw
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 145
ht-degree: 97%

---

# disableThirdPartyCookies{#disablethirdpartycookies}

Un indicador booleano opcional que evita que el servicio de identidad de Experience Cloud devuelva la cookie de terceros demdex.net.

>[!NOTE]
>
>Esta configuración era `idSyncDisable3rdPartySyncing` y pasó a denominarse `disableThirdPartyCookies` en la versión 3.0 del 18 de enero de 2018.

**Sintaxis:** `disableThirdPartyCookies: true|false` (el valor predeterminado es `false`) Para `VisitorAPI.js` v3.0.0 o posterior.

Cuando `disableThirdPartyCookies: true`, el servicio de identidad no devuelve la cookie demdex.net de terceros (consulte [Cookies y el servicio de Experience Cloud ID](../../introduction/cookies.md)). Si el visitante de un sitio tiene ya esta cookie en su explorador, el servicio de ID no la usará para crear un nuevo Experience Cloud ID (MID) o devolver un ID existente. En lugar de eso, el servicio de ID crea un MID aleatorio nuevo en la cookie de origen. Una vez habilitado, pueden recopilarse datos con el servicio de ID para compartirlos en distintas soluciones de Experience Cloud.

**Ejemplo de código**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   disableThirdPartyCookies: true 
});
```

