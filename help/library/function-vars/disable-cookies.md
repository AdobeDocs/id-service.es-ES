---
description: Un indicador booleano opcional que impide que el servicio Experience Cloud ID devuelva la cookie de terceros demdex. net.
keywords: Servicio de ID
seo-description: Un indicador booleano opcional que impide que el servicio Experience Cloud ID devuelva la cookie de terceros demdex. net.
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7 ed 5 aa 16-44 ca -4702-878 a -1 a 208 ca 95270
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# disableThirdPartyCookies{#disablethirdpartycookies}

Un indicador booleano opcional que impide que el servicio Experience Cloud ID devuelva la cookie de terceros demdex. net.

>[!NOTE]
>
>This configuration was `idSyncDisable3rdPartySyncing` and renamed to `disableThirdPartyCookies` in the January 18, 2018 release of v3.0.

**Sintaxis:**`disableThirdPartyCookies: true|false` (el valor predeterminado `false`es.) For `VisitorAPI.js` v1.5.3, or greater.

When `disableThirdPartyCookies: true`, the ID service does not return the third-party, demdex.net cookie (see [Cookies and the Experience Cloud ID Service](../../introduction/cookies.md) ). Si el visitante de un sitio tiene ya esta cookie en su navegador, el servicio de ID no la usará para crear un nuevo Experience Cloud ID (MID) o devolver un ID existente. En lugar de ello, el servicio de ID crea un MID aleatorio nuevo en la cookie de origen. Una vez habilitado, podrá recopilar datos con el servicio de ID y compartirlos entre distintas soluciones de Experience Cloud.

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

