---
description: Versiones de funcionalidades, actualizaciones o cambios en el servicio de Experience Cloud ID para 2017.
keywords: ID Service
seo-description: Versiones de funcionalidades, actualizaciones o cambios en el servicio de Experience Cloud ID para 2017.
seo-title: Notas de la versión 2017
title: Notas de la versión 2017
uuid: 79452df0-49db-42b8-96fe-01aa7629fbb5
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Notas de la versión 2017 {#release-notes}

Versiones de funcionalidades, actualizaciones o cambios en el servicio de Experience Cloud ID para 2017.

Estos cambios también se capturan en las notas [de la versión de](https://docs.adobe.com/content/help/es-ES/release-notes/experience-cloud/current.html)Experience Cloud.

>[!NOTE]
>
>No hay notas de la versión ni cambios de código para los clientes para marzo, abril, mayo u octubre de 2017. En esos meses, el código de servicio de ID se ha mantenido sin cambios en v2.1.

## Versión 2.5 {#section-27b441509124493f80984ed09bd9e88b}

Septiembre de 2017

<!--
<p>
<note type="important">
ID service support for Internet Explorer 6, 7, and 8 is deprecated and will be discontinued in a future release.
</note> </p>
-->

<table id="table_FD24C06C7B3547C3A7673C46B1852A35"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Función </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> getVisitorValues</span> </p> </td> 
   <td colname="col2"> <p>Se trata de una API asíncrona que devuelve identificadores para Analytics, el servicio de ID, la exclusión de la recopilación de datos, la ubicación geográfica y el contenido “blob” de metadatos de forma predeterminada. Además, se puede controlar cuáles son los ID que desea que se devuelvan con la enumeración opcional <span class="codeph">visitor.FIELDS</span>. Consulte <a href="../library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Correcciones de errores y otros cambios**

* Se ha corregido un error relacionado con Chrome que hacía que el servicio de ID generara un error al hacer clic en el botón Atrás de ese explorador.
* El servicio de ID ahora vuelve a activar la sincronización de ID cuando cambia el ID de región en la respuesta de llamada de evento.
* Added new documentation, [Content Security Policies and the Experience Cloud Identity Service](/help/reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3), that explains how to whitelist calls to Adobe domains used by the ID service.

## Versión 2.4 {#section-f4d1608dd8894f558a92b82e83321200}

Agosto de 2017

<table id="table_D9623D34F4444B038F7835750932C8AA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Función </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe</span> </p> </td> 
   <td colname="col2"> <p>Una configuración booleana opcional que determina si el servicio de ID envía datos (o no) a Device Co-Op de Adobe Experience Cloud. Consulte <a href="../library/function-vars/coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local">isCoopSafe</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Documentación revisada**

Se han actualizado y revisado las [preguntas más frecuentes](/help/faq-intro/faq-intro.md) para incluir preguntas más frecuentes por separado para diferentes soluciones de [!DNL Experience Cloud].

## Versión 2.3 {#section-ae7b1cb1e52e4ca5a46b453a3ba1f571}

Julio de 2017

<table id="table_1448040D09B94A74883A694FCF91EB33"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Función </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> sdidParamExpiry</span> </p> </td> 
   <td colname="col2"> <p>Cuando se añade a la función <span class="codeph"> Visitor.getInstance </span>, esta configuración le permite omitir el intervalo de caducidad predeterminado del ID de datos suplementarios (SDID) al pasar dicho ID de una página a otra. Se usa <span class="codeph"> sdidParamExpiry </span> con la función de ayuda <span class="codeph">appendSupplimentalDataTo</span>. Consulte <a href="../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458" format="dita" scope="local"> sdidParamExpiry</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> resetState</span> </p> </td> 
   <td colname="col2"> <p>Esta función se ha diseñado principalmente para ayudar a los clientes de A4T a solucionar los problemas relacionados con el uso de ID en páginas o pantallas únicas, o bien en aplicaciones. Consulte <a href="../library/get-set/resetstate.md#reference-47fc00ae139042d795d78244d9970139" format="dita" scope="local"> resetState</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Correcciones de errores y otros cambios**

* Se ha corregido un error en VisitorAPI.js v2.2 que impedía que el servicio de ID y el Destinatario trabajaran juntos en Internet Explorer.
* Se ha revisado el código para ayudar a mejorar la forma en que el servicio de ID envía datos al iframe de publicación de destino. Esto ayuda a reducir el uso de CPU.

## Version 2.2 {#section-b7dee2495c29470e9b3a3132ec1fd951}

Fecha de lanzamiento: Junio de 2017

<table id="table_7E412383E89D46759B00FE7328C9946F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Función </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/whitelistdomain.md#reference-999899ff7b5b429a8824c9db7a379808" format="dita" scope="local"> whitelistParentDomain y whitelistIframeDomains </a> </p> </td> 
   <td colname="col2"> <p>Estas configuraciones permiten que diferentes instancias del código de servicio de ID implementadas en un iFrame y en la página principal se comuniquen entre sí. Están diseñadas para ayudar a resolver problemas con 2 casos de uso específicos en los que puede que sea posible, o no, controlar la página o el dominio principal y en los que tenga el código de servicio de ID cargando en el iFrame de un dominio que controla. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Actualizaciones de documentación para mayo {#section-1d36b91bb7a140ce8a145251ffac9f2f}

<table id="table_CD031A716A694E8FA89695C9B614BC91"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Tema </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../faq-intro/faq.md" format="dita" scope="local"> Preguntas más frecuentes </a> </p> </td> 
   <td colname="col2"> <p>Se ha actualizado la sección <span class="keyword">Analytics</span> con información sobre cómo encontrar la información sobre el servidor de seguimiento. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Actualizaciones de documentación para abril {#section-df3e5a85448c4001a6791517520ae06e}

<table id="table_ADC2636240654C69B8B6A45849024540"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Tema </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/subdomain-config.md#reference-8ad017b3e5d24d34b3da25e8f8a56196" format="dita" scope="local"> audienceManagerServer y audienceManagerServerSecure </a> </p> </td> 
   <td colname="col2"> <p>Se han agregado vínculos a la documentación de <span class="keyword">Audience Manager</span> que describe las llamadas al dominio <span class="codeph">demdex.net</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <a href="../library/function-vars/subdomain-config.md" format="dita" scope="local"> Conceptos básicos de sincronización de ID y tasas de coincidencia </a> </p> </td> 
   <td colname="col2"> <p>Se ha revisado la sección <span class="keyword">Media Optimizer</span> para describir la llamada a <span class="codeph">cm.eversttech.net</span>. Se trata de la sincronización de ID automática que realiza el servicio de ID con <span class="keyword">Media Optimizer</span>. Esta característica se publicó en enero de 2017. Consulte <a href="../release-notes/notes-2017.md#section-0ceac6007c1241b58ad607e2b76b2b7e" format="dita" scope="local">Versión 2.0</a> más abajo. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Versión 2.1 {#section-5e666dc47c2f4f92999e92697d75799e}

Fecha de lanzamiento: Febrero de 2017

**Funciones**

<table id="table_1F7E1CF091604D22B1D9F3F1AE4DB2D7"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Función </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> Propiedad de la API del servicio de ID, <span class="codeph"> idSyncContainerID</span></p> </td> 
   <td colname="col2"> <p>Esta propiedad define el ID de contenedor que utiliza <span class="keyword"> Audience Manager </span> para sincronizar los ID. Consulte <a href="/help/library/function-vars/idsyncontainerid.md" format="https" scope="external"> idSyncContainerID</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Método de la API del servicio de ID, <span class="codeph">appendSupplementalDataIDTo(<span class="varname"> URL</span>,<span class="varname"> SDID</span>)</span></p> </td> 
   <td colname="col2"> <p>Este método público anexa el <span class="wintitle"> ID de datos adicionales </span> (SDID) como un parámetro de cadena de consulta a una URL de redirección. Consulte <a href="../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d" format="dita" scope="local"> appendSupplementalDataIDTo</a>. (MCID-285) </p> </td> 
  </tr> 
 </tbody> 
</table>

**Correcciones**

Se ha corregido un error que hacía que el servicio de ID realizara llamadas redundantes al servidor para un ID en lugar de usar el ID almacenado en la cookie AMCV. (MCID-296)

**Nueva documentación**

[Uso de la precarga de DNS con diferentes soluciones y servicios de Experience Cloud](https://docs.adobe.com/content/help/en/core-services/interface/more-resources/dns-prefetch.html)

## Versión 2.0 {#section-0ceac6007c1241b58ad607e2b76b2b7e}

Enero de 2017

>[!IMPORTANT]
>
>El código de servicio de ID v2.0 sincroniza automáticamente los ID con Adobe Media Optimizer de forma predeterminada. Eso significa que verá una llamada desde la página a `cm.eversttech.net`, que es un dominio de [!DNL Media Optimizer] heredado controlado por [!DNL Adobe]. Consulte también [Conceptos básicos de sincronización de ID y tasas de coincidencia](../introduction/match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab).

**Correcciones y mejoras**

* Se ha corregido un error que impedía que AppMeasurement realizara llamadas de seguimiento a Analytics. (MCID-254, MCID-256, MCID-286)
* Se ha corregido un error que impedía que el servicio de ID fallara de inmediato si un visitante había habilitado un bloqueador de anuncios y ese bloqueador estaba configurado para excluir el dominio demdex.net. Se trata de un error poco frecuente e inusual porque la mayoría de las herramientas de bloqueo de publicidad no bloquean el dominio demdex.net. (MCID-233)
* Se ha corregido un error debido a las interacciones entre el código de servicio de ID y un script personalizado en el sitio web de un cliente. Este problema impedía que Internet Explorer 9 cargara páginas web. (MCID-206)

## Años anteriores {#section-aaabe2b7b0f04641b24acffc11cd7d2e}

Notas de la versión del servicio de ID anteriores.
