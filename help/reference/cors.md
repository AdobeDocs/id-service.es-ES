---
description: Los navegadores utilizan Cross Origin Resource Sharing (CORS) para solicitar recursos de un dominio que no es el dominio en uso. El servicio de identidad de Experience Cloud admite los estándares CORS que habilitan solicitudes de recursos de origen diverso del lado del cliente. El servicio de ID cambia a solicitudes JSONP en los navegadores más antiguos o que no admiten el mecanismo CORS.
keywords: Servicio de ID
title: Compatibilidad con CORS en el servicio de Experience Cloud ID
exl-id: 0e8ffe85-8d1f-42a0-aae3-a2b3b28c7bce
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Compatibilidad con CORS en el servicio de identidad de Experience Cloud {#cors-support-in-the-experience-cloud-id-service}

Los navegadores utilizan Cross Origin Resource Sharing (CORS) para solicitar recursos de un dominio que no es el dominio en uso. El servicio de identidad de Experience Cloud admite los estándares CORS que habilitan solicitudes de recursos de origen diverso del lado del cliente. El servicio de ID cambia a solicitudes JSONP en los navegadores más antiguos o que no admiten el mecanismo CORS.

## Problemas con políticas del mismo origen y solicitudes del servicio de ID {#section-6608cf46d27143eeaeabacaa6aa14e8e}

Las políticas del mismo origen son controles de seguridad o restricciones que aplica un explorador web. Cuando se aplica en este nivel, el propio explorador web determina si se permitirá o bloqueará una solicitud de recursos realizada de una página a otra. Para determinar si una solicitud es del mismo origen, el explorador compara:

* Identificadores de recursos uniformes (URI)
* Nombres de host (por ejemplo, http://www.my-webpage-example.com)
* Números de puerto (por ejemplo, puerto 80 y 440 para solicitudes HTTP y HTTPS)

El explorador permite que una solicitud se realice correctamente si ambas páginas comparten estas características y bloquea las solicitudes de recursos si no lo hacen.

## CORS resuelve problemas con políticas del mismo origen  {#section-76c87ec3295d447bab220c84f138c235}

CORS es una forma segura y eficaz de solicitar recursos en distintos dominios. La especificación CORS incluye un conjunto de encabezados HTTP que los exploradores utilizan para enviar, recibir y evaluar solicitudes de recursos. Evaluar una solicitud de recurso es lo que se conoce como *`preflight check`*. Esta comprobación permite a los exploradores y servidores determinar qué solicitudes están permitidas o bloqueadas. La comprobación preliminar es transparente para la aplicación, la API o el script que solicita un recurso. Dos encabezados importantes en el proceso de solicitud de recursos son:

* `Origin`: un encabezado de solicitud que identifica el origen de una solicitud.
* `Access-Control-Allow-Origin`: un encabezado de respuesta que indica si se puede compartir un recurso con el solicitante.

Veamos el funcionamiento de estos encabezados. En este ejemplo, supongamos que tenemos una empresa de servicios financieros que ha implementado el servicio de [!DNL Experience Cloud] ID de en su sitio, www.finance-website.com. La siguiente tabla define cómo los encabezados de solicitud y respuesta CORS comprueban el acceso a un recurso.

<table id="table_B004ACF52B5A4D33B1DCF7EA77BE4E6D"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Acción </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Solicitud</b> </p> </td> 
   <td colname="col2"> <p>Cuando se carga la página de la empresa de finanzas, el navegador realiza una solicitud a <span class="codeph">dpm.demdex.net</span>. Se trata de una llamada al dominio de los servidores de recopilación de datos (DCS) que utiliza el servicio de ID. Esta solicitud entre dominios incluye el encabezado: </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Origin: https://www.finance-website.com</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Respuesta</b> </p> </td> 
   <td colname="col2"> <p>La respuesta del dominio DCS incluye estos encabezados que proporcionan al sitio de la empresa financiera acceso a los recursos necesarios: </p> <p> 
     <ul class="simplelist"> 
      <li> <span class="codeph"> Access-Control-Allow-Origin: https://www.finance-website.com</span> </li> 
      <li> <span class="codeph"> Access-Control-Allow-Credentials: true</span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

Consulte también [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa).

## Otras ventajas al usar CORS {#section-6f44f30694c44f95bf9854b8a2af8449}

La tabla siguiente describe algunas de las ventajas que CORS ofrece a los clientes que utilizan el servicio de ID.

<table id="table_AEB51A263D454F90B66E8C8D0513CF79"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Ventaja </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><b>Mayor seguridad</b> </p> </td> 
   <td colname="col2"> <p>CORS utiliza <a href="https://developer.mozilla.org/es-ES/docs/Web/API/XMLHttpRequest" format="https" scope="external"> XMLHttpRequest</a> para solicitar y transferir datos. Este método es más seguro que una solicitud JSONP. Garantiza que no hay forma de ejecutar JavaScript arbitrario, que podría estar contenido en la respuesta del DCS. La carga útil de respuesta CORS XMLHttpRequest la analiza el JavaScript del servicio de ID y no se ejecuta simplemente en una función de llamada de retorno. </p> <p> <p>Nota: Para aceptar cookies, el objeto <span class="codeph">XMLHttpRequest</span> tiene que tener su propiedad <span class="codeph">withCredentials</span> establecida en <span class="codeph">true</span>. Esta propiedad es compatible con Chrome, Firefox, Internet Explorer (v10+), Opera y Safari. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>Mejoras en el rendimiento</b> </p> </td> 
   <td colname="col2"> <p>CORS ayuda a mejorar el rendimiento por estos motivos: </p> 
    <ul id="ul_EC3A178003A94D70883B914050D7C464"> 
     <li id="li_F8B44352BFBB46CDBD07AE40B9F2D0EC">El explorador gestiona las solicitudes de recursos. El proceso de solicitud es transparente para el servicio de ID. </li> 
     <li id="li_C63E43A4CAB84210AB6A39100E5864BE">A diferencia de las solicitudes JSONP asincrónicas, el explorador no anula la prioridad de las solicitudes CORS ni las pone en cola. </li> 
     <li id="li_1A2A15F591B84D1BAED3CFAB391EEBEC">El servicio de ID responde permisivamente. Esto significa que, cuando se ha pasado una URL como <span class="codeph">Origin</span>, el servicio de ID concederá a la página acceso a los recursos solicitados. </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
