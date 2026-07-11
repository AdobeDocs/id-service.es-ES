---
description: Versiones de funcionalidades, actualizaciones o cambios en el servicio de ID de visitante para 2016.
keywords: Servicio de ID de visitante
title: Notas de la versión 2016
feature-set: Experience Cloud Services
feature: TK421
exl-id: f96b9869-6282-4090-b392-797608e25a51
TQID: https://experienceleague.adobe.com/u91aLAt-ycKk1U1A1yhAVUAonGhV6fHWNRVTZB0QAXI
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 1114
ht-degree: 47%

---

# Notas de la versión 2016 {#release-notes}

Versiones de funcionalidades, actualizaciones o cambios en el servicio de ID de visitante para 2016.

Estos cambios también se registran en las [notas de la versión de CX Enterprise](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=es).

## Versión 1.10 {#section-7d719b3213344a46858835042e0214ed}

Noviembre de 2016

>[!IMPORTANT]
>
>* La versión 1.10 requiere [!UICONTROL AppMeasurement] 1.8.0.
>* Al usar la versión 2.0.0 o posterior de la biblioteca del servicio de ID de visitante, la sincronización de ID para Adobe Media Optimizer se iniciará de forma predeterminada. Consulte [Conceptos básicos de sincronización de ID y tasas de coincidencia](/help/introduction/match-rates.md).

**Correcciones y mejoras**

* Se han añadido instrucciones sobre cómo implementar el servicio de ID de visitante en un entorno de lado de servidor.
* Se ha agregado `Visitor.overwriteCrossDomainMCIDAndAID`, una función booleana que le permite sobrescribir los ECID e ID de Analytics en otros de sus dominios. Consulte [Sobrescribir ID del visitante](../library/function-vars/overwrite-visitor-id.md#reference-9db13d637ce44fb6a8d519de5743ccde).

* Se ha añadido la `TS = UTC`Marca de fecha y hora como propiedad de la función `visitor.appendVisitorIDsTo`. El servicio de ID de visitante utiliza la marca de tiempo para determinar si debe utilizar los ID en la URL de redireccionamiento en función de un intervalo de antigüedad de 5 minutos. Consulte [Función para asignar un ID de visitante](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce).

* Se ha añadido `Visitor.getLocationHint,` una función nueva que devuelve un ID de región. Consulte [Obtener ID de región (ubicación)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c)

* Se han agregado las funciones `idSyncByURL` e `idSyncByDataSource`, que permiten implementar manualmente la sincronización de ID en el iFrame de publicación de destino. Consulte [Sincronización de ID por dirección URL o fuente de datos](../library/get-set/idsync.md#reference-b01b88c083434cf8abbeabd3c6956c48).

* Se ha corregido un error que bloqueaba la llamada de seguimiento AppMeasurement cuando `disableThirdPartyCalls:true`.
* Se ha corregido un error que impedía que el servicio de ID de visitante pasara el ECID a través de dominios diferentes.

## Versión 1.9.0 {#section-04e1b4d4b10d40468f2116b8119998e7}

Octubre de 2016

**Correcciones y mejoras**

* Se ha corregido un error que pasaba ID de usuarios únicos de Audience Manager (AAMUUID) como ECID al servicio de ID de visitante.
* Si el tiempo TTL (time-to-live) para una cookie AMCV ha caducado, el servicio de ID de visitante seguirá devolviendo esa información al servidor siempre y cuando la cookie contenga un ECID. Después de esta llamada, el servicio de ID de visitante realiza una llamada asincrónica para actualizar la cookie. Esto ayuda a mejorar el rendimiento, ya que el servicio de ID de visitante no tiene que esperar una respuesta del servidor. Puede usar valores de cookies de AMCV existentes y luego solicitar una actualización.
* El servicio de ID de visitante sincroniza automáticamente los ECID con Adobe Media Optimizer y otros dominios internos de Adobe directamente en la página. La sincronización automática está habilitada para todas las cuentas existentes y nuevas. Esto ayuda a mejorar las tasas de coincidencia para Media Optimizer. Se aplica a `VisitorAPI.js` versión 1.8, o posterior. Consulte también [Conceptos básicos de sincronización de ID y tasas de coincidencia](../introduction/match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab).

**Documentación nueva y revisada**

**Nuevo:** [Obtención de ID de región y de usuario desde la cookie de AMCV](../reference/regions.md#concept-15b2c8c894b846a48f1f61a353cfdf4e)

## Versión 1.8.0 {#section-69f2eb5b246b4c7aafe116b7a2a5448a}

Septiembre de 2016

**Correcciones y mejoras**

Se ha añadido `disableThirdPartyCalls` como indicador booleano opcional que puede establecer en la función `Visitor.getInstance`. Cuando `disableThirdPartyCalls= true`, el servicio de ID de visitante no realizará llamadas a otros dominios. De forma predeterminada, `disableThirdPartyCalls= false`. Consulte [disableThirdPartyCalls](../library/function-vars/disablethirdpartycalls.md#reference-fba90b095e9746daad46e3abb790d18b).

## Versión 1.7.0 {#section-f7d59104de6644fca3691480383d4644}

Agosto de 2016

**Correcciones y mejoras**

* Se ha añadido `idSyncAttachIframeOnWindowLoad` como una bandera booleana opcional, que puede establecer en la función de `Visitor.getInstance`. Cuando `idSyncAttachIframeOnWindowLoad= true`, el servicio de ID de visitante carga el iFrame de sincronización de ID en la ventana de carga. De forma predeterminada, el servicio de ID de visitante carga el iFrame lo más rápido posible. Este indicador *sustituye* el `idSyncAttachIframeASAP` en desuso. Consulte [Variables de función Visitor.getInstance](../library/function-vars/function-vars.md).

* Funcionalidad agregada para admitir el seguimiento de ECID entre dominios, aplicaciones nativas e híbridas, y transiciones web. Consulte [Función de ayuda para asignar un ID de visitante](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce).

* Se han agregado funciones al código `VisitorAPI.js` que determinan si el servicio de ID de visitante ha generado el ECID de visitante en el lado del cliente o del servidor, o si se agotó el tiempo de espera de las llamadas de ID. Consulte las [funciones de seguimiento de tiempo de espera](../library/get-set/timeout-functions.md#reference-912bae0f116540df8c5dc1c008656c23) y [la generación de seguimiento de la ID de visitante del lado del cliente](../library/get-set/client-side-id.md#reference-8244dc6d832c4bbaaa97528096bcc2a6).

**Documentación nueva y revisada**

Revisado: [Requisitos del servicio de identificación de visitante](../reference/requirements.md)

**Problemas conocidos**

Los clientes que usan código DIL de Audience Manager y código `VisitorAPI.js` en la misma página deben establecer la variable de DIL `secureDataCollection= false`. Consulte [secureDataCollection](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-overview.html?lang=es).

## Versión 1.6.0 {#section-3faaa14bf3934c6a99b8f79ee06fc0d2}

Julio de 2016

>[!IMPORTANT]
>
>La versión 1.6.0 del servicio de ID de visitante *requiere* AppMeasurement para JavaScript versión 1.6.2. Si actualiza al servicio de ID de visitante versión 1.6.0, asegúrese de que está empleando la versión de código de AppMeasurement correcta.

<table id="table_5472AAFA0DD2495DB8D92DEBE44A07A9"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Función </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Intercambio de recursos de origen cruzado (CORS) </p> </td> 
   <td colname="col2"> <p>El mecanismo CORS permite a los navegadores solicitar recursos provenientes de un dominio distinto al actual. El servicio de ID de visitante admite los estándares CORS para habilitar solicitudes de recursos de origen diverso del lado del cliente. El servicio de ID de visitante cambia a solicitudes JSONP en los navegadores que no admiten el mecanismo CORS. </p> <p>Consulte: </p> 
    <ul id="ul_15386385108F4E07824041DD6F2DC11E"> 
     <li id="li_DB8D5AA4A7004DE4AE9CBC31A389F5BD"> <a href="../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758" format="dita" scope="local"> Compatibilidad con CORS en el servicio de ID de visitante </a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**Correcciones y mejoras**

* Se ha agregado un parámetro `d_fieldgroup` a las llamadas de sincronización con el ID en `dpm.demdex.net`. Este nuevo parámetro se utiliza para realizar tareas internas de depuración y resolución de problemas.

* Se ha agregado un atributo de título al iFrame del servicio de ID de visitante. El título de iFrame ayuda a los lectores de pantalla a proporcionar información sobre la página a los usuarios que necesiten ayuda para interactuar con contenido en línea. El atributo de título de iFrame se establece en `Adobe ID Syncing iFrame`.
* Se ha agregado `idSyncAttachIframeASAP: true` como opción que se puede definir en la función `Visitor.getInstance`. Cuando `true`, el servicio de ID de visitante carga el iFrame de sincronización de ID lo más rápido posible. De esta forma se pretenden mejorar los porcentajes de coincidencia de la sincronización con el ID. De forma predeterminada, el servicio de ID de visitante carga el iFrame en la carga de ventana. Consulte [Variables de función Visitor.getInstance](../library/function-vars/function-vars.md).

* Se ha corregido un error relativo a una función de rellamada que hacía que AppMeasurement se quedara detenido en un bucle infinito.
* Se ha cambiado el valor predeterminado `loadTimeout` a 30.000 milisegundos (de 500 milisegundos). Consulte [Variables de función Visitor.getInstance](../library/function-vars/function-vars.md).

**Documentación nueva y revisada**

**Nuevas**

* [Implementación del servicio de ID de visitante para Analytics, Audience Manager y Target](../implementation-guides/setup-aam-analytics-target.md#concept-e7e2dc0d0bbe481db93328b5604b4673)

**Revisado**

* [Requisitos del servicio de ID de visitante](../reference/requirements.md)
* [Comprobación y verificación del servicio de ID de visitante](../implementation-guides/test-verify.md)

## Versión 1.5.7 {#section-735b4989a5744a42aeb2d97602dbda62}

Junio de 2016

<table id="table_5D604D0820C84EC996ACB99126C8A3DF"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Función </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Cambios en el atributo <span class="codeph">iframe.sandbox</span> </p> </td> 
   <td colname="col2"> <p>Se ha configurado el iFrame para que <span class="codeph">iframe.sandbox='allow-scripts allow-same-origin'; </span>. </p> <p>El hecho de permitir únicamente estos dos tokens ayuda a mejorar la seguridad y proporciona al servicio de ID de visitante la funcionalidad básica necesaria para la sincronización de ID. </p> <p>El atributo de zona protegida no es compatible con Internet Explorer versión 9 o anteriores. Para obtener más información, consulte la sección Atributos de esta <a href="https://developer.mozilla.org/es-ES/docs/Web/HTML/Element/iframe" format="https" scope="external">documentación de iFrame</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Codificación del ECID </p> </td> 
   <td colname="col2"> <p>El servicio de ID de visitante codifica el valor de MID devuelto por el servidor o cuando lo establece la función <span class="codeph"> visitor.setMarketingCloudVisitorID() </span>. Para obtener más información sobre MID, consulte <a href="../introduction/cookies.md" format="dita" scope="local"> cookies y ECID </a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Correcciones**

El API de visitante ya no fuerza una llamada de resincronización extra con Audience Manager cuando no hay un ID de visitante de Analytics anterior.

## Versión 1.5.x {#section-a62ae48275324058b57edf66ee5a579f}

Mayo de 2016

**Actualizaciones de documentación**

* [Requisitos de SDK para Android e iOS](../reference/requirements.md#section-73b2446fba8e463888642c7d7dfd94f1)
* [Comprobación y verificación del servicio de ID de visitante](../implementation-guides/test-verify.md)

## Versión 1.5.x {#section-0cfeef085cff4cbc8dff6cbc6fc32920}

Abril de 2016

**Actualizaciones de documentación**

[Implementación del servicio de ID de visitante para Target](../implementation-guides/setup-target.md#concept-9b5a802132574e1181927ddd00e5c5af)

## Versión 1.5.4 {#section-1a44ba147fb3440ea7dec551faee3528}

Marzo de 2016

<table id="table_F4ED1F88709E4D3BA69C747879A4E18F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Función </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Compatibilidad con la exclusión </p> </td> 
   <td colname="col2"> <p>El servicio de ID de visitante admite las solicitudes de anulación de la suscripción de visitantes. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> Cambio del intervalo de sincronización de ID </p> </td> 
   <td colname="col2"> <p>El servicio de ID de visitante ahora realiza llamadas de sincronización de ID en cada llamada a los servidores de recopilación de datos. Anteriormente, el servicio de ID de visitante solo realizaba una solicitud en la primera llamada para obtener un ECID. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Versión 1.5.3 {#section-7c09ba2832bd4644a1ccc3aa83abe66a}

Enero de 2016

**Actualizaciones de documentación**

<table id="table_C1A5DBED6B104C0FBA54EC663D3B0E86"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Tema </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../reference/authenticated-state.md" format="dita" scope="local"> ID de cliente y estados de autenticación </a> </p> </td> 
   <td colname="col2"> <p>Texto revisado. Los ID de cliente solo deben pasarse como valores no codificados. Los ID de codificación crearán identificadores con codificación doble. </p> </td> 
  </tr> 
 </tbody> 
</table>


