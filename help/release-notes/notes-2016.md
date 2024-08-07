---
description: Versiones de funcionalidades, actualizaciones o cambios en el servicio de identidad de Experience Cloud para 2016.
keywords: Servicio de ID
title: Notas de la versión 2016
feature-set: Experience Cloud Services
feature: TK421
exl-id: f96b9869-6282-4090-b392-797608e25a51
source-git-commit: d027f7fca8cf62d6b5d80ec3c37049ddd1afdd70
workflow-type: tm+mt
source-wordcount: '1175'
ht-degree: 100%

---

# Notas de la versión 2016 {#release-notes}

Versiones de funcionalidades, actualizaciones o cambios en el servicio de identidad de Experience Cloud para 2016.

Estos cambios también se recopilan en las [notas de la versión de Experience Cloud](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=es).

## Versión 1.10 {#section-7d719b3213344a46858835042e0214ed}

Noviembre de 2016

>[!IMPORTANT]
>
>* La versión 1.10 requiere [!UICONTROL AppMeasurement] 1.8.0.
>* Al usar la versión 2.0.0 (o una posterior) de la biblioteca del servicio de identidad de Experience Cloud, la sincronización de ID para Adobe Media Optimizer se iniciará de forma predeterminada. Consulte [Conceptos básicos de sincronización de ID y tasas de coincidencia](/help/introduction/match-rates.md).

**Correcciones y mejoras**

* Instrucciones adicionales sobre cómo implementar el servicio de ID en entornos de lado de servidor.
* Se ha agregado `Visitor.overwriteCrossDomainMCIDAndAID`, una función booleana que permite sobrescribir los ID de Experience Cloud e ID de Analytics en otros de sus dominios. Consulte [Sobrescribir ID del visitante](../library/function-vars/overwrite-visitor-id.md#reference-9db13d637ce44fb6a8d519de5743ccde).

* Se ha añadido la `TS = UTC`Marca de fecha y hora como propiedad de la función `visitor.appendVisitorIDsTo`. El servicio de ID utiliza la marca de fecha y hora para determinar si debe utilizar los ID en la dirección URL de redireccionamiento en función de un intervalo de antigüedad de 5 minutos. Consulte [Función para asignar un ID de visitante](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce).

* Se ha añadido `Visitor.getLocationHint,` una función nueva que devuelve un ID de región. Consulte [Obtener ID de región (ubicación)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c)

* Se han agregado las funciones `idSyncByURL` e `idSyncByDataSource`, que permiten implementar manualmente la sincronización de ID en el iFrame de publicación de destino. Consulte [Sincronización de ID por dirección URL o fuente de datos](../library/get-set/idsync.md#reference-b01b88c083434cf8abbeabd3c6956c48).

* Se ha corregido un error que bloqueaba la llamada de seguimiento AppMeasurement cuando `disableThirdPartyCalls:true`.
* Se ha corregido un problema que impedía que el servicio de ID pasara el Experience Cloud ID (MID) entre dominios distintos.

## Versión 1.9.0 {#section-04e1b4d4b10d40468f2116b8119998e7}

Octubre de 2016

**Correcciones y mejoras**

* Se ha corregido un error que pasaba ID de usuarios únicos de Audience Manager (AAMUUID) como Experience Cloud ID al servicio de ID.
* Aunque el tiempo TTL (time-to-live) para una cookie AMCV haya expirado, el servicio de ID seguirá devolviendo esa información al servidor siempre y cuando la cookie contenga un Experience Cloud ID. Después de esta llamada, el servicio de ID realiza una llamada asincrónica para actualizar la cookie. Esto ayuda a mejorar el rendimiento, ya que el servicio de ID no tiene que esperar una respuesta del servidor. Puede usar valores de cookies de AMCV existentes y luego solicitar una actualización.
* El servicio de ID sincroniza automáticamente los Experience Cloud ID (MID) con Adobe Media Optimizer y otros dominios internos de Adobe directamente en la página. La sincronización automática está habilitada para todas las cuentas existentes y nuevas. Esto ayuda a mejorar las tasas de coincidencia para Media Optimizer. Se aplica a VisitorAPI.js versión 1.8, o posteriores. Consulte también [Conceptos básicos de sincronización de ID y tasas de coincidencia](../introduction/match-rates.md#concept-e55cf228b90c457fbee8c3cb06b195ab).

**Documentación nueva y revisada**

**Nuevo:** [Obtención de ID de región y de usuario desde la cookie de AMCV](../reference/regions.md#concept-15b2c8c894b846a48f1f61a353cfdf4e)

## Versión 1.8.0 {#section-69f2eb5b246b4c7aafe116b7a2a5448a}

Septiembre de 2016

**Correcciones y mejoras**

Se ha añadido `disableThirdPartyCalls` como indicador booleano opcional que puede establecer en la función `Visitor.getInstance`. Si el método `disableThirdPartyCalls= true`, el servicio de ID no llama a otros dominios. De forma predeterminada, `disableThirdPartyCalls= false`. Consulte [disableThirdPartyCalls](../library/function-vars/disablethirdpartycalls.md#reference-fba90b095e9746daad46e3abb790d18b).

## Versión 1.7.0 {#section-f7d59104de6644fca3691480383d4644}

Agosto de 2016

**Correcciones y mejoras**

* Se ha añadido `idSyncAttachIframeOnWindowLoad` como una bandera booleana opcional, que puede establecer en la función de `Visitor.getInstance`. Cuando `idSyncAttachIframeOnWindowLoad= true`, el servicio de ID carga la sincronización iFrame de ID en la ventana de carga. El servicio de ID carga el iFrame lo más rápido posible de forma predeterminada. Este indicador *sustituye* el `idSyncAttachIframeASAP` en desuso. Consulte [Variables de función Visitor.getInstance](../library/function-vars/function-vars.md).

* Funcionalidad agregada para admitir un seguimiento de los ID de [!DNL Experience Cloud] entre dominios, aplicaciones nativas e híbridas, y transiciones web. Consulte [Función de ayuda para asignar un ID de visitante](../library/get-set/appendvisitorid.md#reference-ff167ef19e37433fb08ac2b5a86229ce).

* Funciones agregadas para el código VisitorAPI.js que determinan si el servicio de ID ha generado el ID de [!DNL Experience Cloud] del lado del cliente o lado del servidor, o si se agotó el tiempo de espera de las llamadas de ID. Consulte las [funciones de seguimiento de tiempo de espera](../library/get-set/timeout-functions.md#reference-912bae0f116540df8c5dc1c008656c23) y [la generación de seguimiento de la ID de visitante del lado del cliente](../library/get-set/client-side-id.md#reference-8244dc6d832c4bbaaa97528096bcc2a6).

**Documentación nueva y revisada**

Revisado: [Requisitos del servicio de identidad de Experience Cloud](../reference/requirements.md)

**Problemas conocidos**

Los clientes que utilizan código DIL de [!DNL Audience Manager] y código visitorAPI.js en la misma página, deben establecer la variable DIL `secureDataCollection= false`. Consulte [secureDataCollection](https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-overview.html?lang=es).

## Versión 1.6.0 {#section-3faaa14bf3934c6a99b8f79ee06fc0d2}

Julio de 2016

>[!IMPORTANT]
>
>La versión 1.6.0 del servicio de [!DNL Experience Cloud] ID de *requiere* AppMeasurement para JavaScript versión 1.6.2. Si actualiza al servicio de ID versión 1.6.0, asegúrese de que está empleando la versión de código de AppMeasurement correcta.

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
   <td colname="col2"> <p>El mecanismo CORS permite a los navegadores solicitar recursos provenientes de un dominio distinto al actual. El servicio de identidad de Experience Cloud admite los estándares CORS para habilitar solicitudes de recursos de origen diverso del lado del cliente. El servicio de ID cambia a solicitudes JSONP en los navegadores que no admiten el mecanismo CORS. </p> <p>Consulte: </p> 
    <ul id="ul_15386385108F4E07824041DD6F2DC11E"> 
     <li id="li_DB8D5AA4A7004DE4AE9CBC31A389F5BD"> <a href="../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758" format="dita" scope="local"> Compatibilidad con CORS en el servicio de identidad de Experience Cloud ID</a> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**Correcciones y mejoras**

* Se ha agregado un parámetro `d_fieldgroup` a las llamadas de sincronización con el ID en `dpm.demdex.net`. Este nuevo parámetro se utiliza para realizar tareas internas de depuración y resolución de problemas.

* Se ha agregado un atributo de título al iFrame del servicio de ID. El título de iFrame ayuda a los lectores de pantalla a proporcionar información sobre la página a los usuarios que necesiten ayuda para interactuar con contenido en línea. El atributo de título de iFrame se establece en `Adobe ID Syncing iFrame`.
* Se ha agregado `idSyncAttachIframeASAP: true` como opción que se puede definir en la función `Visitor.getInstance`. Cuando se define como `true`, el servicio de ID carga el iFrame de sincronización con el ID lo más rápido posible. De esta forma se pretenden mejorar los porcentajes de coincidencia de la sincronización con el ID. De forma predeterminada, el servicio de ID carga el iFrame en la carga de ventana. Consulte [Variables de función Visitor.getInstance](../library/function-vars/function-vars.md).

* Se ha corregido un error relativo a una función de rellamada que hacía que AppMeasurement se quedara detenido en un bucle infinito.
* Se ha cambiado el valor predeterminado `loadTimeout` a 30.000 milisegundos (de 500 milisegundos). Consulte [Variables de función Visitor.getInstance](../library/function-vars/function-vars.md).

**Documentación nueva y revisada**

**Nuevas**

* [Implementación del servicio de identidad de Experience Cloud para Analytics](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd)
* [Implementación del servicio de identidad de Experience Cloud para Analytics, Audience Manager y Target](../implementation-guides/setup-aam-analytics-target.md#concept-e7e2dc0d0bbe481db93328b5604b4673)

**Revisado**

* [Requisitos del servicio de identidad de Experience Cloud](../reference/requirements.md)
* [Comprobación y verificación del servicio de identidad de Experience Cloud](../implementation-guides/test-verify.md)

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
   <td colname="col2"> <p>Se ha configurado el iFrame para que <span class="codeph">iframe.sandbox='allow-scripts allow-same-origin'; </span>. </p> <p>El hecho del permitir solo estos dos testigos ayuda a mejorar la seguridad y proporciona al servicio de ID la funcionalidad básica necesaria para la sincronización de ID. </p> <p>El atributo de zona protegida no es compatible con Internet Explorer versión 9 o anteriores. Para obtener más información, consulte la sección Atributos de esta <a href="https://developer.mozilla.org/es-ES/docs/Web/HTML/Element/iframe" format="https" scope="external">documentación de iFrame</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Codificación del Experience Cloud ID (MID) </p> </td> 
   <td colname="col2"> <p>El servicio de ID codifica el valor de MID cuando el servidor lo devuelve o cuando está configurado por la función <span class="codeph">visitor.setMarketingCloudVisitorID()</span>. Para obtener más información sobre MID, consulte <a href="../introduction/cookies.md" format="dita" scope="local">Cookies e Experience Cloud ID</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Correcciones**

El API de visitante ya no fuerza una llamada de resincronización extra con Audience Manager cuando no hay un ID de visitante de Analytics anterior.

## Versión 1.5.x {#section-a62ae48275324058b57edf66ee5a579f}

Mayo de 2016

**Actualizaciones de documentación**

* [Requisitos de SDK para Android e iOS](../reference/requirements.md#section-73b2446fba8e463888642c7d7dfd94f1)
* [Data Workbench y el servicio de identidad de Experience Cloud](../reference/dwb.md#task-72df50a051944a47b01b0c0bc3d1e1d8)
* [Comprobación y verificación del servicio de identidad de Experience Cloud](../implementation-guides/test-verify.md)

## Versión 1.5.x {#section-0cfeef085cff4cbc8dff6cbc6fc32920}

Abril de 2016

**Actualizaciones de documentación**

[Implementación del servicio de identidad de Experience Cloud para Target](../implementation-guides/setup-target.md#concept-9b5a802132574e1181927ddd00e5c5af)

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
   <td colname="col2"> <p>El servicio de <span class="keyword">Experience Cloud</span> ID admite las solicitudes de anulación de la suscripción de visitantes. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> Cambio del intervalo de sincronización de ID </p> </td> 
   <td colname="col2"> <p>El servicio de <span class="keyword">Experience Cloud ID</span> ahora realiza llamadas de sincronización de ID en cada llamada a los servidores de recopilación de datos. Anteriormente, el servicio de ID solo realizaba una solicitud en la primera llamada para obtener un <span class="keyword">Experience Cloud ID</span>. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Actualizaciones de documentación**

* [Implementación del servicio de identidadde Experience Cloud para](../implementation-guides/setup-analytics.md#concept-9ebbea85cb844a15b557be572cd142fd): nuevo procedimiento que describe cómo configurar el servicio de identidad con [!DNL Analytics].

* [Puntos de decisión para la migración del servicio de identidad de Experience Cloud](../reference/analytics-reference/migration-decisions.md#concept-ba44803eea3c4cc185232a510cec0257): texto revisado para una mayor claridad. Trabajar con un solo dominio significa que puede dejar de utilizar un CNAME de recopilación de datos si ya no desea administrarlo. Sin embargo, no es necesario cambiar si su CNAME funciona.

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
