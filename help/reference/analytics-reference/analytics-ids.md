---
description: El servicio de identidad de Experience Cloud sustituye a los métodos de ID de visitante de Analytics anteriores.
keywords: Servicio de ID
seo-description: El servicio de identidad de Experience Cloud sustituye a los métodos de ID de visitante de Analytics anteriores.
seo-title: Configuración de ID de Analytics y de Experience Cloud
title: Configuración de ID de Analytics y de Experience Cloud
uuid: 421cf597-a3e0-4ca3-8ce8-d0c80cbb6aca
translation-type: ht
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# Configuración de ID de Analytics y de Experience Cloud{#setting-analytics-and-experience-cloud-ids}

El servicio de Experience Cloud ID sustituye a los métodos de ID de visitante de Analytics anteriores.

Una vez implementado el servicio de ID, este código se ejecuta antes de AppMeasurement. El servicio de ID recupera los Experience Cloud ID y Analytics para que los valores estén listos cuando se cargue AppMeasurement.

Cuando AppMeasurement se carga, los valores de los Experience Cloud ID y de Analytics se solicitan al servicio de ID y se envían a la recopilación de datos con cada llamada del servidor. El servicio de ID determina el ID de visitante y lo pasa a AppMeasurement directamente, por lo que este servicio debe incluirse e implementarse en todas las páginas antes que el archivo JavaScript de AppMeasurement.

## Cambios en el proceso de ID de Analytics {#section-79bb86ae63f546419bb1a7ef5e710462}

El cambio principal consiste en que, al migrar al servicio de ID de [!DNL Experience Cloud], la cookie de ID se establece mediante JavaScript y no en el encabezado HTTP que devuelve el servidor web de recopilación de datos. Para explicar este cambio, en las secciones siguientes se describe cómo se establecen las cookies con estos dos métodos.

**Encabezado HTTP**

Una respuesta de HTTP de un servidor web establece las cookies en un explorador. Así es como se establece la `s_vi` cookie. La `s_vi` cookie identifica a los visitantes de Analytics. Cuando se establece una cookie, esta se envía con todas las solicitudes HTTP subsiguientes a este servidor.

Cuando se envía una solicitud al servidor de recopilación de datos de Adobe, se comprueba la existencia de la cookie `s_vi` en el encabezado. Si la cookie se encuentra en la solicitud, se usa para identificar al visitante. En caso contrario, el servidor genera un ID de [!DNL Experience Cloud] único, lo establece como una cookie en el encabezado de respuesta HTTP y lo devuelve con la solicitud. La cookie se almacena en el explorador y se envía de vuelta al servidor de recopilación de datos en las visitas subsiguientes al sitio. Este proceso permite la identificación del visitante en cada visita.

No obstante, hay exploradores como Apple Safari que no aceptan cookies de terceros. Hablamos de cookies que se establecen en el explorador desde dominios ajenos al sitio web actual. Asimismo, Safari bloquea las cookies en dominios de terceros si un visitante no había estado antes en dicho dominio. Por ejemplo, si está en `mysite.com` y el servidor de recopilación de datos es `mysite.omtrdc.net`, el explorador puede rechazar la cookie que se devuelve en el encabezado HTTP desde `mysite.omtrdc.net`.

Para evitarlo, muchos clientes han implementado registros CNAME para sus servidores de recopilación de datos. Esto puede ser una parte efectiva de una [implementación de una cookie de origen](https://marketing.adobe.com/resources/help/en_US/whitepapers/first_party_cookies/). Si se configura la asignación de un registro CNAME a un nombre de host en el dominio del cliente para el servidor de recopilación de datos (por ejemplo, si se asigna `metrics.mysite.com` a `mysite.omtrdc.net`), se almacenará la cookie de ID de [!DNL Experience Cloud], porque ahora coinciden los dominios de recopilación de datos y del sitio web. De este modo, se incrementa la probabilidad de que se almacene la cookie del servicio de ID. Sin embargo, esto conlleva cierta sobrecarga, pues se necesita configurar los registros CNAME y mantener certificados SSL para los servidores de recopilación de datos.

**JavaScript**

JavaScript puede leer y escribir las cookies establecidas en el dominio de origen (el dominio del sitio web actual). El servicio de ID de [!DNL Experience Cloud] usa este método para establecer la cookie `AMCV_###@AdobeOrg` que contiene todos los ID de visitante, de modo que el dominio del servidor de seguimiento puede almacenar la cookie de ID de visitante sin necesidad de coincidir con el dominio del sitio web. En la mayoría de los casos, este es el método preferido para establecer la cookie del servicio de ID porque se elimina la sobrecarga de registros CNAME y certificados SSL.

No obstante, en ciertas situaciones puede resultar ventajoso establecer la cookie en el encabezado HTTP para realizar un seguimiento entre dominios. Estos casos se describen en [CNAME de recopilación de datos y seguimiento entre dominios](../../reference/analytics-reference/cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d).

## ID de Analytics personalizados {#section-b6a7bd19e9ff432390010062450808f6}

El establecimiento de un ID de cliente mediante `s.visitorID` es un método para identificar a los usuarios en Analytics. Sin embargo, las integraciones en las que se exportan o importan datos de Analytics mediante el servicio de ID no funcionarán cuando se identifique a un visitante mediante `s.visitorID`.

Entre ellas se cuentan las audiencias compartidas, Análisis para objetivo (A4T) y atributos del cliente. Estas integraciones no admiten la configuración de un ID de Analytics personalizado.

## Pedido de ID de visitante de Analytics {#section-de1dc9fc9b6d4388995b70e35b8bcddf}

Una vez implementado el servicio de ID de visitante, los visitantes de Analytics se pueden identificar de cinco formas distintas, que se detallan, en orden de preferencia, en la tabla siguiente:

<table id="table_D267D36451F643D1BB68AF6FEAA6AD1A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Orden utilizado </th> 
   <th colname="col2" class="entry"> Parámetro de consulta (método de recopilación) </th> 
   <th colname="col3" class="entry"> Presente si </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <img id="image_9F3E58898A1B4F40BBDEF5ADE362E55C" src="assets/step1_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/es_ES/sc/implement/?f=visid_custom" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p>Se establece s.visitorID. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_77A06981672745B6AEA8BB4D55911CCA" src="assets/step2_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/es_ES/sc/implement/?f=visid_analytics" format="http" scope="external"> aid (cookie s_vi)</a> </p> </td> 
   <td colname="col3"> <p>El visitante ya tenía una cookie s_vi antes de implementar el servicio de <span class="keyword">Experience Cloud ID</span> o bien ya tenía configurado un <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local">período de gracia</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_0A950B1A6B004387AFEE8EED882739CB" src="assets/step3_icon.png" /> </p> </td> 
   <td colname="col2"> <p>mid (cookie AMCV_ establecida por el servicio de ID de visitante de Experience Cloud) </p> </td> 
   <td colname="col3"> <p>El explorador del visitante acepta cookies de origen </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_6F0ED8FE3EF846CA8E6ECCC3C0070D85" src="assets/step4_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/es_ES/sc/implement/?f=visid_fallback" format="http" scope="external"> fid (cookie de seguridad en H.25.3 o posterior, o AppMeasurement para JavaScript)</a> </p> </td> 
   <td colname="col3"> <p>Un navegador no acepta cookies de terceros y el servidor de seguimiento de Analytics está configurado como servidor de seguimiento de terceros. </p> <p> <p>Nota: El valor <span class="codeph">fid</span> es un identificador preexistente y no se utiliza si se ha implementado el servicio de ID en el sitio. En este caso, el <span class="codeph">fid</span> no es necesario porque la cookie <a href="../../introduction/cookies.md" format="dita" scope="local"> AMCV de origen</a> hace que quede obsoleto. Se ha mantenido para admitir código heredado y por motivos históricos. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <img id="image_23D8C0EB69EC4084BC237B5B98C036F4" src="assets/step5_icon.png" /> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/es_ES/sc/implement/?f=visid_fallback" format="http" scope="external"> Dirección IP, agente de usuario y dirección IP de puerta de enlace</a> </p> </td> 
   <td colname="col3"> <p>El explorador del visitante no acepta cookies. </p> </td> 
  </tr> 
 </tbody> 
</table>

En muchos escenarios, es posible que vea dos o tres ID distintos en una llamada, pero Analytics utilizará el primer ID presente en la lista como el ID de [!DNL Experience Cloud] oficial. Por ejemplo, si configura un ID de visitante personalizado (incluido en el parámetro de consulta "vid"), ese ID se utilizará antes que otros ID que puedan existir en la misma visita.

>[!MORE_LIKE_THIS]
>
>* [Orden de operaciones para los ID de Analytics](../../reference/analytics-reference/analytics-order-of-operations.md#concept-b92935b4fff545adb4773f3728bc15ef)

