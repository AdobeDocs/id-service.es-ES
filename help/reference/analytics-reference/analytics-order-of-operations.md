---
description: Tras implementar el servicio de ID de visitante, hay cinco maneras de identificar a los visitantes en Analytics.
keywords: Servicio de ID
seo-description: Tras implementar el servicio de ID de visitante, hay cinco maneras de identificar a los visitantes en Analytics.
seo-title: Orden de operaciones para los ID de Analytics
title: Orden de operaciones para los ID de Analytics
uuid: cb1d136e-093f-43b0-a7e1-96f1e61fdad0
translation-type: ht
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# Orden de operaciones para los ID de Analytics{#order-of-operations-for-analytics-ids}

Tras implementar el servicio de ID de visitante, hay cinco maneras de identificar a los visitantes en Analytics.

En muchos escenarios, es posible que vea dos o tres ID distintos en una llamada, pero Analytics utilizará el primer ID presente en la lista como el ID de [!DNL Experience Cloud] oficial. Por ejemplo, si está configurando un ID de visitante personalizado (incluido en el `vid` parámetro de consulta), ese ID se utilizará antes de otros ID que pudiera haber en esa misma visita. Consulte [Configuración de ID de Analytics y de Experience Cloud](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6) para obtener más información.

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
   <td colname="col1"> <p> <b>1.<sup>o</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/es_ES/sc/implement/?f=visid_custom" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p><span class="codeph">s.visitorID</span> se ha establecido. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>2.<sup>o</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/es_ES/sc/implement/?f=visid_analytics" format="http" scope="external"> aid (cookie s_vi)</a> </p> </td> 
   <td colname="col3"> <p>El visitante ya tenía una cookie s_vi antes de implementar el servicio de <span class="keyword">Experience Cloud ID</span> o bien ya tenía configurado un <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local">período de gracia</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>3.<sup>o</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="../../introduction/cookies.md#section-7ff7d96d6e4141b08a84a75a63d7814c" format="dita" scope="local"> servicio de Experience Cloud ID (MID) </a> </p> </td> 
   <td colname="col3"> <p>El explorador del visitante acepta cookies de origen. Esto lo establece la cookie de AMCV. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>4.<sup>o</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/es_ES/sc/implement/?f=visid_fallback" format="http" scope="external"> fid (cookie de seguridad en H.25.3 o posterior, o AppMeasurement para JavaScript)</a> </p> </td> 
   <td colname="col3"> <p>Un navegador no acepta cookies de terceros y el servidor de seguimiento de Analytics está configurado como servidor de seguimiento de terceros. </p> <p> <p>Nota: El valor <span class="codeph">fid</span> es un identificador preexistente y no se utiliza si se ha implementado el servicio de ID en el sitio. En este caso, el <span class="codeph">fid</span> no es necesario porque la cookie <a href="../../introduction/cookies.md" format="dita" scope="local"> AMCV de origen</a> hace que quede obsoleto. Se ha mantenido para admitir código heredado y por motivos históricos. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>5.<sup>o</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://marketing.adobe.com/resources/help/es_ES/sc/implement/?f=visid_fallback" format="http" scope="external"> Dirección IP, agente de usuario y dirección IP de puerta de enlace</a> </p> </td> 
   <td colname="col3"> <p>El explorador del visitante no acepta cookies. </p> </td> 
  </tr> 
 </tbody> 
</table>

