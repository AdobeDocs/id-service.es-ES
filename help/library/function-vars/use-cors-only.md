---
description: Un indicador booleano opcional que controla el modo en el que el navegador solicita recursos desde el servicio de identidad de Experience Cloud.
keywords: Servicio de ID
seo-description: Un indicador booleano opcional que controla el modo en el que el navegador solicita recursos desde el servicio de Experience Cloud ID.
seo-title: useCORSOnly
title: useCORSOnly
uuid: 607dc035-dffc-4f4d-be51-08ef6c0a8fad
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# useCORSOnly{#usecorsonly}

Un indicador booleano opcional que controla el modo en el que el navegador solicita recursos desde el servicio de Experience Cloud ID.

**Sintaxis:** `useCORSOnly: true|false` (el valor predeterminado es `false`)

**Información general**

Cuando se establece en `false`, el navegador comprueba los recursos con CORS o JSONP. No obstante, el servicio de ID siempre intenta solicitar recursos con CORS primero. Vuelve a JSONP en navegadores anteriores que no son compatibles con CORS. Si necesita forzar al navegador para que use solo CORS, establezca `useCORSOnly:true` en la llamada de la función `Visitor.getInstance`.

>[!IMPORTANT]
>
>`Set useCORSOnly: true` si tiene requisitos de seguridad estrictos. Solo debe habilitar este modo si está seguro de que todos los visitantes utilizan navegadores compatibles con CORS. La experiencia del usuario no se ve afectada cuando se usan navegadores no compatibles con CORS. No obstante, los navegadores que no son compatibles con CORS no podrán solicitar recursos o intercambiar datos con [!DNL Adobe Experience Cloud].

**Ejemplo de código**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   trackingServer: "Insert tracking server here here",  //Same as s.trackingServer 
   trackingServerSecure: "Insert secure tracking server here",  //Same as s.trackingServerSecure 
 
   //For CNAME support only. Exclude these variables if you're not using CNAME 
   marketingCloudServer: "Insert tracking server here", 
   marketingCloudServerSecure: "Insert secure tracking server here", 
 
   //Function variable 
   useCORSOnly: true 
});
```

