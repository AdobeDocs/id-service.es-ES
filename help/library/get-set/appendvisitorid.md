---
description: Esta función le permite compartir un Experience Cloud ID de un visitante entre dominios cuando los navegadores bloquean las cookies de terceros. Para utilizar esta función, debe haber implementado el servicio de ID y ser el propietario de los dominios de origen y destino. Disponible en VisitorAPI.js versión 1.7.0 o posteriores.
keywords: Servicio de ID
seo-description: Esta función le permite compartir un Experience Cloud ID de un visitante entre dominios cuando los navegadores bloquean las cookies de terceros. Para utilizar esta función, debe haber implementado el servicio de ID y ser el propietario de los dominios de origen y destino. Disponible en VisitorAPI.js versión 1.7.0 o posteriores.
seo-title: appendVisitorIDsTo (seguimiento entre dominios)
title: appendVisitorIDsTo (seguimiento entre dominios)
uuid: 06b453ee-73c5-4625-82d9-877ad2b4f702
exl-id: 3e4f4e2c-e658-4124-bd0e-59c63127bdde
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '448'
ht-degree: 100%

---

# appendVisitorIDsTo (seguimiento entre dominios) {#appendvisitoridsto-cross-domain-tracking}

Esta función le permite compartir un Experience Cloud ID de un visitante entre dominios cuando los navegadores bloquean las cookies de terceros. Para utilizar esta función, debe haber implementado el servicio de ID y ser el propietario de los dominios de origen y destino. Disponible en VisitorAPI.js versión 1.7.0 o posteriores.

Contenido:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-7251d88befd440b4b79520e33c5aa44a" format="dita" scope="local"> Realizar el seguimiento de los visitantes entre dominios cuando los navegadores bloquean las cookies de terceros </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-62d55f7f986542b0b9238e483d50d7b0" format="dita" scope="local"> Anexar el ejemplo de código de ID de visitante </a> </li> 
 <li> <a href="../../library/get-set/appendvisitorid.md#section-168e313df6054af0a7e27b9fa0d69640" format="dita" scope="local"> Compatibilidad con Dynamic Tag Management (DTM) y SDK </a> </li> 
</ul>

## Realizar el seguimiento de los visitantes entre dominios cuando los navegadores bloquean las cookies de terceros {#section-7251d88befd440b4b79520e33c5aa44a}

El servicio de identidad escribe una cookie propia y de terceros en el explorador cuando una persona visita su sitio (consulte [Cookies y el servicio de identidad de Experience Cloud](../../introduction/cookies.md)). La cookie de origen contiene el MID, un ID único para ese visitante. La cookie de terceros contiene otro ID utilizado por el servicio de ID para generar el MID. Cuando un explorador bloquea esta cookie de terceros, el servicio de ID no puede:

* Volver a generar el ID único para ese visitante del sitio cuando navegue a otro dominio.
* Rastrear visitantes en diferentes dominios propiedad de la organización.

Para ayudar a resolver este problema, implemente una ` Visitor.appendVisitorIDsTo( *`URL`*)`. Esta propiedad permite que el servicio de ID rastree los visitantes del sitio en varios dominios, incluso cuando sus exploradores bloquean las cookies de terceros. Funciona de esta forma:

* A medida que un visitante navega a sus otros dominios, la ` Visitor.appendVisitorIDsTo( *`URL`*)` adjunta el MID como parámetro de consulta en el redireccionamiento de URL desde el dominio original al dominio de destino.
* Este código de servicio de ID en el dominio de destino extrae el MID de la URL, en lugar de enviar una solicitud a Adobe para obtener el ID del visitante en cuestión. Esta solicitud incluye el ID de la cookie de terceros, que no está disponible en este caso.
* El código de servicio de ID en la página de destino emplea el MID transferido para hacer un seguimiento del visitante.

Consulte el ejemplo de código para obtener más información.

## Anexar el ejemplo de código de ID de visitante {#section-62d55f7f986542b0b9238e483d50d7b0}

El ejemplo siguiente puede ayudarle a empezar con las ` Visitor.appendVisitorIDsTo( *`URL`*)`. Cuando se implementa adecuadamente, su código JavaScript podría ser similar al del siguiente ejemplo.

```js
//Code on Domain A 
var destinationURL = "www.destination.com"; 
 
//Call the ID service 
var visitor = Visitor.getInstance(...); 
 
//Append visitor IDs to the destination URL 
var destinationURLWithVisitorIDs = visitor.appendVisitorIDsTo(destinationURL); 
     //Result of appendVisitorIDsTo includes destination URL, Experience Cloud ID (MCMID), and Analytics ID (MCAID) 
     "www.destination.com?adobe_mc=MCMID=1234|MCAID=5678"
//Redirect to the destination
```

## Compatibilidad con Dynamic Tag Management (DTM) y SDK {#section-168e313df6054af0a7e27b9fa0d69640}

<table id="table_6E7152B4FD2B4C4D8C9477C68204C4FF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Compatibilidad con </th> 
   <th colname="col2" class="entry"> Consulte </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>DTM</b> </p> </td> 
   <td colname="col2"> <p> <a href="https://helpx.adobe.com/es/dtm/kb/how-to-set-marketing-cloud-id-service-helper-function-in-adobe-d.html" format="https" scope="external"> Configuración de la función appendVisitorIDTo en DTM </a> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>SDK</b> </p> </td> 
   <td colname="col2"> 
    <ul id="ul_9D7933FF68EE4C71BAE999B3747F8398"> 
     <li id="li_9036C76AAECC4E639C23020C0C9F2AF8"> <a href="https://docs.adobe.com/content/help/es-ES/mobile-services/android/experience-cloud-android/mc-methods.html" format="https" scope="external"> Métodos del servicio de ID de Android </a> </li> 
     <li id="li_E49D357905584674BFDFE348345B3849"> <a href="https://docs.adobe.com/content/help/es-ES/mobile-services/ios/exp-cloud-ios/mc-methods.html" format="https" scope="external"> Métodos del servicio de ID de iOS </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
