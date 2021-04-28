---
description: Un indicador booleano opcional que evita que el servicio de Experience Cloud ID devuelva la cookie de terceros demdex.net.
keywords: Servicio de ID
seo-description: Un indicador booleano opcional que evita que el servicio de Experience Cloud ID devuelva la cookie de terceros demdex.net.
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7ed5aa16-44ca-4702-878a-1a208ca95270
exl-id: 19d12822-0e17-4a1c-8e9c-25a22e20a4a8
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '157'
ht-degree: 100%

---

# disableThirdPartyCookies {#disablethirdpartycookies}

Un indicador booleano opcional que evita que el servicio de Experience Cloud ID devuelva la cookie de terceros demdex.net.

>[!NOTE]
>
>Esta configuración era `idSyncDisable3rdPartySyncing` y pasó a denominarse `disableThirdPartyCookies` en la versión 3.0 del 18 de enero de 2018.

**Sintaxis:** `disableThirdPartyCookies: true|false` (el valor predeterminado es `false`) Para `VisitorAPI.js` v3.0.0 o posterior.

Cuando `disableThirdPartyCookies: true`, el servicio de identidad no devuelve la cookie demdex.net de terceros (consulte [Cookies y el servicio de identidad de Experience Cloud](../../introduction/cookies.md)). Si el visitante de un sitio tiene ya esta cookie en su explorador, el servicio de ID no la usará para crear un nuevo Experience Cloud ID (MID) o devolver un ID existente. En lugar de eso, el servicio de ID crea un MID aleatorio nuevo en la cookie de origen. Una vez activado, pueden recopilarse datos con el servicio de ID para compartirlos en distintas soluciones de Experience Cloud.

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
