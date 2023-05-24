---
description: Un indicador booleano opcional que controla el modo en el que el navegador solicita recursos desde el servicio de Experience Cloud ID.
keywords: Servicio de ID
title: useCORSOnly
exl-id: 049a082a-8e6b-44cc-bd05-c12aaf3cbe4d
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 100%

---

# useCORSOnly{#usecorsonly}

Un indicador booleano opcional que controla el modo en el que el navegador solicita recursos desde el servicio de Experience Cloud ID.

**Sintaxis:** `useCORSOnly: true|false` (el valor predeterminado es `false`)

**Información general**

Cuando se establece en `false`, el navegador comprueba los recursos con CORS o JSONP. Sin embargo, el servicio de ID siempre intenta solicitar recursos con CORS primero. Vuelve a JSONP en navegadores más antiguos que no admiten CORS. Si necesita forzar al navegador para que use solo CORS, establezca `useCORSOnly:true` en la llamada de la función `Visitor.getInstance`.

>[!IMPORTANT]
>
>`Set useCORSOnly: true` si tiene requisitos de seguridad estrictos. Solo debe habilitar este modo si está seguro de que los visitantes del sitio utilizan navegadores compatibles con CORS. La experiencia del usuario no se ve afectada por los navegadores que no admiten CORS. No obstante, los navegadores que no son compatibles con CORS no podrán solicitar recursos o intercambiar datos con [!DNL Adobe Experience Cloud].

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
