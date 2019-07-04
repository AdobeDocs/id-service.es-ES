---
description: Un indicador booleano opcional que evita que el servicio Experience Cloud ID devuelva la cookie de terceros demdex.net.
keywords: Servicio de ID
seo-description: Un indicador booleano opcional que evita que el servicio Experience Cloud ID devuelva la cookie de terceros demdex.net.
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7ed5aa16-44ca-4702-878a-1a208ca95270
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# disableThirdPartyCookies{#disablethirdpartycookies}

Un indicador booleano opcional que evita que el servicio Experience Cloud ID devuelva la cookie de terceros demdex.net.

>[!NOTE]
>
>Esta configuración era `idSyncDisable3rdPartySyncing` y pasó a denominarse `disableThirdPartyCookies` en la versión 3.0 del 18 de enero de 2018.

**Sintaxis:** `disableThirdPartyCookies: true|false` (el valor predeterminado es `false`) Para `VisitorAPI.js` v1.5.3 o posterior.

Cuando `disableThirdPartyCookies: true`, el servicio de ID no devuelve la cookie demdex.net de terceros (consulte [Cookies y el servicio Experience Cloud ID](../../mcvid-introduction/mcvid-cookies.md)). Si el visitante de un sitio tiene ya esta cookie en su navegador, el servicio de ID no la usará para crear un nuevo Experience Cloud ID (MID) o devolver un ID existente. En lugar de ello, el servicio de ID crea un MID aleatorio nuevo en la cookie de origen. Una vez habilitado, podrá recopilar datos con el servicio de ID y compartirlos entre distintas soluciones de Experience Cloud.

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

