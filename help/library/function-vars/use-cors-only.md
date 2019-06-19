---
description: Un indicador booleano opcional que controla cómo solicita el navegador los recursos desde el servicio de identidad de Experience Platform.
keywords: Servicio de ID
seo-description: Un indicador booleano opcional que controla cómo solicita el navegador los recursos desde el servicio de identidad de Experience Platform.
seo-title: useCORSOnly
title: useCORSOnly
uuid: 607 dc 035-dffc -4 f 4 d-be 51-08 ef 6 c 0 a 8 fad
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# useCORSOnly{#usecorsonly}

Un indicador booleano opcional que controla cómo solicita el navegador los recursos desde el servicio de identidad de Experience Platform.

**Sintaxis:**`useCORSOnly: true|false` (el valor predeterminado `false`es.)

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

