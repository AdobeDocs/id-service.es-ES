---
description: Necesaria para dominios de nivel superior y de múltiples partes, donde alguna de las dos últimas partes de la URL tiene más de dos caracteres.
keywords: Servicio de ID
seo-description: Necesaria para dominios de nivel superior y de múltiples partes, donde alguna de las dos últimas partes de la URL tiene más de dos caracteres.
seo-title: cookieDomain
title: cookieDomain
uuid: a57e5477-c07b-4d54-8aea-8e8b152f1423
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# cookieDomain{#cookiedomain}

Necesaria para dominios de nivel superior y de múltiples partes, donde alguna de las dos últimas partes de la URL tiene más de dos caracteres.

**Sintaxis:** ` cookieDomain: " *`URL`*"` (el prefijo `www` no es obligatorio).

**Caso de uso**

* Requerido: `www.example.com.uk`
* No obligatorio: `www.example.co.uk`

**Ejemplo de código**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   cookieDomain:"example.com.uk" 
});
```

