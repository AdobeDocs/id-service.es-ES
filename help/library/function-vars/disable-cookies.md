---
description: Un indicador booleano opcional que impide que el servicio de identidad de Experience Platform devuelva la cookie de terceros demdex. net.
keywords: Servicio de ID
seo-description: Un indicador booleano opcional que impide que el servicio de identidad de Experience Platform devuelva la cookie de terceros demdex. net.
seo-title: disableThirdPartyCookies
title: disableThirdPartyCookies
uuid: 7 ed 5 aa 16-44 ca -4702-878 a -1 a 208 ca 95270
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# disableThirdPartyCookies{#disablethirdpartycookies}

Un indicador booleano opcional que impide que el servicio de identidad de Experience Platform devuelva la cookie de terceros demdex. net.

>[!NOTE]
>
>Esta configuración se ha cambiado `idSyncDisable3rdPartySyncing` de nombre `disableThirdPartyCookies` en la versión del 18 de enero de 2018 de la versión v 3.0.

**Sintaxis:**`disableThirdPartyCookies: true|false` (el valor predeterminado `false`es.) Para `VisitorAPI.js` la versión 1.5.3 o superior.

Cuando `disableThirdPartyCookies: true`, el servicio de ID no devuelve la cookie demdex. net de terceros (consulte [Cookies y el servicio](../../introduction/cookies.md) de identidad de Experience Platform). Si el visitante de un sitio tiene ya esta cookie en su navegador, el servicio de ID no la usará para crear un nuevo Experience Cloud ID (MID) o devolver un ID existente. En lugar de ello, el servicio de ID crea un MID aleatorio nuevo en la cookie de origen. Una vez habilitado, podrá recopilar datos con el servicio de ID y compartirlos entre distintas soluciones de Experience Cloud.

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

