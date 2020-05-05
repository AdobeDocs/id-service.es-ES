---
description: Antes de implementar el servicio de identidad de Experience Cloud, es necesario que conozca cómo afecta este servicio al seguimiento de visitantes en dominios múltiples y los problemas potenciales si recopila datos con distintos métodos o a través de archivos JavaScript.
keywords: ID Service
seo-description: Antes de implementar el servicio de Experience Cloud ID, es necesario que conozca cómo afecta este servicio al seguimiento de visitantes en dominios múltiples y los problemas potenciales si recopila datos con distintos métodos o a través de archivos JavaScript.
seo-title: Puntos de decisión para la migración del servicio de identidad de Experience Cloud
title: Puntos de decisión para la migración del servicio de identidad de Experience Cloud
uuid: ee56b5de-fcf3-4cfb-9e53-762af7c4d2ff
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Puntos de decisión para la migración del servicio de Experience Cloud ID

Antes de implementar el servicio de Experience Cloud ID, es necesario que conozca cómo afecta este servicio al seguimiento de visitantes en dominios múltiples y los problemas potenciales si recopila datos con distintos métodos o a través de archivos JavaScript.

Responda a las preguntas de esta sección para poder determinar si debe realizar algún paso adicional para la migración.

## ¿Tiene un CNAME de recopilación de datos?

Muchos clientes pueden dejar de utilizar un CNAME de recopilación de datos como parte de la migración del servicio de ID.

<table id="table_13F7C1E3D64D4F86B0149C9D3B54AADD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Método de recopilación de datos </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Con un CNAME </p> </td> 
   <td colname="col2"> <p>Consulte la siguiente pregunta para decidir si debe dejar de utilizar un CNAME de recopilación de datos. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Sin un CNAME </p> </td> 
   <td colname="col2"> <p>Pase a la sección <a href="../../reference/analytics-reference/migration-decisions.md#section-34dabde7780e4a339f134c0ca7768961" format="dita" scope="local">Si no tiene un CNAME de recopilación de datos, ¿su servidor de recopilación de datos es *.2o7.net o *.sc.omtrdc.net?</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Si tiene un CNAME de recopilación de datos, ¿tiene varios dominios?

Si tiene varios dominios que envían datos al *mismo grupo* de informes, le recomendamos que recopile datos con un CNAME. Esto le ayuda a realizar el seguimiento de visitantes entre dominios. Si recopila datos en un único dominio, no tiene ninguna ventaja mantener un CNAME de recopilación de datos.

<table id="table_D132BCA243E54657AEC930559343FDD3"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Recopilación de datos de </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Varios dominios </p> </td> 
   <td colname="col2"> <p>Si está realizando un seguimiento de visitantes en varios dominios y también tiene un sitio de entrada principal en el que se puede identificar a los clientes antes de que visiten otros dominios, debe seguir utilizando el CNAME de recopilación de datos. Consulte <a href="../../reference/analytics-reference/cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d" format="dita" scope="local">CNAME de recopilación de datos y seguimiento entre dominios</a> para obtener una descripción detallada. </p> <p>Tenga en cuenta que necesitará especificar dos parámetros de servidor de seguimiento adicionales, <span class="codeph">visitor.marketingCloudServer</span> y <span class="codeph">visitor.marketingCloudServerSecure</span>, para poder configurar un CNAME con el servicio de ID. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Un solo dominio </p> </td> 
   <td colname="col2"> <p>Trabajar con un solo dominio significa que puede dejar de utilizar un CNAME de recopilación de datos si ya no desea administrarlo. Sin embargo, no es necesario cambiar si su CNAME funciona. </p> <p>Si elimina el CNAME: </p> 
    <ul id="ul_12CDECEFC7BB41A18895B507CAA42315"> 
     <li id="li_32E2CD3E58454E20A642BADE507AE86E">Asegúrese de que su nuevo servidor de seguimiento sea <a href="https://docs.adobe.com/content/help/en/analytics/technotes/rdc/regional-data-collection.html" format="https" scope="external">compatible con RDC</a>. </li> 
     <li id="li_865BB6DAA3594EBBAB688E73C8343762">Pásese del CNAME a un servidor de seguimiento de RDC con unos meses de adelanto a la migración al servicio de <span class="keyword">Experience Cloud ID</span>. </li> 
     <li id="li_284A015177554C848C8648DC5BBAA365"> <i>No</i> utilice un servidor de seguimiento <span class="codeph">*.2o7.net</span>. </li> 
     <li id="li_B1ABF03DC46C42059F61542CDE0FE5A1">Contacte con el <a href="https://helpx.adobe.com/es/marketing-cloud/contact-support.html" format="https" scope="external">Servicio de atención al cliente</a> para configurar una migración de visitante. De este modo, obtendrá recuentos de visitantes fiables. </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## ¿Tiene varios archivos JavaScript de Analytics o realiza un seguimiento de aplicaciones o vídeos Flash?

Si tiene varios archivos JavaScript de Analytics o aplicaciones o vídeos Flash en el sitio que envíen datos al *mismo grupo de informes*, debe configurar un período de gracia para que se siga identificando a los visitantes con un ID de Analytics mientras implementa el servicio de ID de [!DNL Experience Cloud].

<table id="table_8A4EA063AF4345B69BC98537E2E702BA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Recopilación de datos con </th> 
   <th colname="col2" class="entry"> Acciones necesarias </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> 
    <ul id="ul_910DD99E074E49C6907F86426EFA5BF2"> 
     <li id="li_4366CC8EB7A54A959568E3761ABBBF23">Varios archivos de JavaScript de Analytics </li> 
     <li id="li_B8A8132019EA48088E4F37E36F153D76">Otros métodos de recopilación de datos </li> 
    </ul> </td> 
   <td colname="col2"> <p>Debe configurar un período de gracia del servicio de ID de visitante para poder implementar el servicio de ID de visitante en cada archivo JavaScript y en otras bibliotecas de recopilación de datos. See <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> ID Service Grace Period</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Un solo archivo JavaScript de Analytics </p> </td> 
   <td colname="col2"> <p>Puede actualizar el archivo JavaScript único para utilizar el servicio de ID de visitante sin un período de gracia. </p> </td> 
  </tr> 
 </tbody> 
</table>

## ¿Está utilizando métodos de recopilación de datos no admitidos?

Es posible que deba actualizar la forma en que realiza el seguimiento de vínculos o dejar de utilizar Sliverlight.

<table id="table_A72AEB92F48345DD83F136B9989F4EF9"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Método de recopilación de datos </th> 
   <th colname="col2" class="entry"> Acciones necesarias </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>JavaScript y/o Flash </p> </td> 
   <td colname="col2"> <p>None. El servicio de <span class="keyword">Experience Cloud ID</span> es compatible con estos métodos de recopilación de datos. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Silverlight </p> </td> 
   <td colname="col2"> <p>Es necesario que migre de Silverlight si los visitantes pueden acceder a contenido de Silverlight y otras secciones de su sitio que utilizan el servicio de <span class="keyword">Experience Cloud ID</span>. El servicio de ID no admite Silverlight. </p> <p> Si está rastreando un reproductor de vídeo basado en Silverlight, es probable que el proveedor proporcione API de JavaScript que puede utilizar en su lugar. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Etiquetas de imágenes predefinidas </p> </td> 
   <td colname="col2"> <p>Actualice los vínculos codificados para utilizar JavaScript. </p> </td> 
  </tr> 
 </tbody> 
</table>

