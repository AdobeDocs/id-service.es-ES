---
description: Tras implementar el servicio de ID de visitante, hay cinco maneras de identificar a los visitantes en Analytics.
keywords: Servicio de ID
title: Orden de operaciones para los ID de Analytics
exl-id: 8ee340fe-ef3b-40e6-9441-7ee0c9e20357
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: ht
source-wordcount: '300'
ht-degree: 100%

---

# Orden de operaciones para los ID de Analytics {#order-of-operations-for-analytics-ids}

Tras implementar el servicio de ID de visitante, hay cinco maneras de identificar a los visitantes en Analytics.

En muchos escenarios, es posible que vea dos o tres ID distintos en una llamada, pero Analytics utilizará el primer ID presente en la lista como el ID de [!DNL Experience Cloud] oficial. Por ejemplo, si está configurando un ID de visitante personalizado (incluido en el `vid` parámetro de consulta), ese ID se utilizará antes de otros ID que pudiera haber en esa misma visita. Consulte [Configuración de Analytics y Experience Cloud ID](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6) para obtener más información.

<table id="table_D267D36451F643D1BB68AF6FEAA6AD1A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Pedido utilizado </th> 
   <th colname="col2" class="entry"> Parámetro de consulta (método de recopilación) </th> 
   <th colname="col3" class="entry"> Presente cuando </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>1<sup>º</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/visitorid.html?lang=es" format="http" scope="external"> vid (s.visitorID)</a> </p> </td> 
   <td colname="col3"> <p><span class="codeph">s.visitorID</span> se ha establecido. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>2.<sup>o</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/core-services/interface/ec-cookies/cookies-analytics.html?lang=es" format="http" scope="external"> aid (cookie s_vi)</a> </p> </td> 
   <td colname="col3"> <p>El visitante ya tenía una cookie s_vi antes de implementar el servicio de <span class="keyword">Experience Cloud ID</span> o bien ya tenía configurado un <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local">período de gracia</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>3.<sup>o</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="../../introduction/cookies.md#section-7ff7d96d6e4141b08a84a75a63d7814c" format="dita" scope="local"> servicio de Experience Cloud ID (MID) </a> </p> </td> 
   <td colname="col3"> <p>El explorador del visitante acepta cookies de origen. Esto lo establece la cookie AMCV. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>4<sup>º</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/analytics-ids.html?lang=es" format="http" scope="external"> fid (cookie de seguridad en H.25.3 o posterior, o AppMeasurement para JavaScript)</a> </p> </td> 
   <td colname="col3"> <p>Un navegador no acepta cookies de terceros y el servidor de seguimiento de Analytics está configurado como servidor de seguimiento de terceros. </p> <p> <p>Nota: El valor <span class="codeph">fid</span> es un identificador preexistente y no se utiliza si se ha implementado el servicio de ID en el sitio. En este caso, el <span class="codeph">fid</span> no es necesario porque la cookie <a href="../../introduction/cookies.md" format="dita" scope="local"> AMCV de origen</a> hace que quede obsoleto. Se ha mantenido para admitir código heredado y por motivos históricos. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>5<sup>º</sup></b> </p> </td> 
   <td colname="col2"> <p> <a href="https://experienceleague.adobe.com/docs/analytics/technotes/visitor-identification.html?lang=es" format="http" scope="external"> Dirección IP, agente de usuario y dirección IP de puerta de enlace</a> </p> </td> 
   <td colname="col3"> <p>El explorador del visitante no acepta cookies. </p> </td> 
  </tr> 
 </tbody> 
</table>
