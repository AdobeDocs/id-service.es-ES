---
description: Antes de implementar el servicio Experience Cloud ID, debe comprender cómo afecta este servicio el seguimiento de visitantes en varios dominios y los posibles problemas si recopila datos con distintos métodos o mediante archivos JavaScript.
keywords: Servicio de ID
seo-description: Antes de implementar el servicio Experience Cloud ID, debe comprender cómo afecta este servicio el seguimiento de visitantes en varios dominios y los posibles problemas si recopila datos con distintos métodos o mediante archivos JavaScript.
seo-title: Puntos de decisión para la migración del servicio Experience Cloud ID
title: Puntos de decisión para la migración del servicio Experience Cloud ID
uuid: ee 56 b 5 de-fcf 3-4 cfb -9 e 53-762 af 7 c 4 d 2 ff
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Puntos de decisión para la migración del servicio Experience Cloud ID

Antes de implementar el servicio Experience Cloud ID, debe comprender cómo afecta este servicio el seguimiento de visitantes en varios dominios y los posibles problemas si recopila datos con distintos métodos o mediante archivos JavaScript.

Responda a las preguntas de esta sección para poder determinar si debe realizar algún paso adicional para la migración.

## ¿Tiene un CNAME de recopilación de datos?

Muchos clientes pueden dejar de utilizar un CNAME de recopilación de datos como parte de la migración al servicio de ID.

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
   <td colname="col2"> <p>Consulte la pregunta siguiente para decidir si debe dejar de utilizar un CNAME de recopilación de datos. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Sin un CNAME </p> </td> 
   <td colname="col2"> <p>Pase a la sección <a href="../../reference/analytics-reference/migration-decisions.md#section-34dabde7780e4a339f134c0ca7768961" format="dita" scope="local">Si no tiene un CNAME de recopilación de datos, ¿su servidor de recopilación de datos es *.2o7.net o *.sc.omtrdc.net?</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Si tiene un CNAME de recopilación de datos, ¿dispone de varios dominios?

Si cuenta con varios dominios que envían datos al *mismo grupo de informes*, le recomendamos una recopilación de datos con un CNAME. Le permitirá realizar el seguimiento de los visitantes entre dominios. Si recopila datos en un único dominio, no obtendrá ninguna ventaja por mantener un CNAME de recopilación de datos.

<table id="table_D132BCA243E54657AEC930559343FDD3"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Recopilación de datos desde </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Varios dominios </p> </td> 
   <td colname="col2"> <p>Si realiza un seguimiento de los visitantes en varios dominios y tiene también un sitio de entrada principal en el que se puede identificar a los clientes antes de que visiten otros dominios, es conveniente que continúe utilizando el CNAME de recopilación de datos. Consulte <a href="../../reference/analytics-reference/cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d" format="dita" scope="local">CNAME de recopilación de datos y seguimiento entre dominios</a> para obtener una descripción detallada. </p> <p>Tenga en cuenta que necesitará especificar dos parámetros de servidor de seguimiento adicionales, <span class="codeph">visitor.marketingCloudServer</span> y <span class="codeph">visitor.marketingCloudServerSecure</span>, para poder configurar un CNAME con el servicio de ID. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Un solo dominio </p> </td> 
   <td colname="col2"> <p>Al trabajar con un solo dominio puede migrarse desde un CNAME de recopilación de datos si ya no desea seguir administrándolo. Sin embargo, no es un requisito cambiar si su CNAME funciona correctamente. </p> <p>Si no elimina el CNAME: </p> 
    <ul id="ul_12CDECEFC7BB41A18895B507CAA42315"> 
     <li id="li_32E2CD3E58454E20A642BADE507AE86E">Asegúrese de que su nuevo servidor de seguimiento sea <a href="https://marketing.adobe.com/resources/help/en_US/whitepapers/rdc/" format="https" scope="external">compatible con RDC</a>. </li> 
     <li id="li_865BB6DAA3594EBBAB688E73C8343762">Pásese del CNAME a un servidor de seguimiento de RDC con unos meses de adelanto a la migración al servicio de ID de <span class="keyword">Experience Cloud</span>. </li> 
     <li id="li_284A015177554C848C8648DC5BBAA365"> <i>No</i> utilice un servidor de seguimiento <span class="codeph">*.2o7.net</span>. </li> 
     <li id="li_B1ABF03DC46C42059F61542CDE0FE5A1">Contacte con el <a href="https://helpx.adobe.com/marketing-cloud/contact-support.html" format="https" scope="external">Servicio de atención al cliente</a> para configurar una migración de visitante. De este modo, obtendrá recuentos de visitantes fiables. </li> 
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
   <th colname="col2" class="entry"> Acciones requeridas </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> 
    <ul id="ul_910DD99E074E49C6907F86426EFA5BF2"> 
     <li id="li_4366CC8EB7A54A959568E3761ABBBF23">Varios archivos de Javascript de Analytics </li> 
     <li id="li_B8A8132019EA48088E4F37E36F153D76">Otros métodos de recopilación de datos </li> 
    </ul> </td> 
   <td colname="col2"> <p>Debe configurar un período de gracia del servicio de ID de visitante para poder implementar el servicio de ID de visitante en cada archivo JavaScript y en otras bibliotecas de recopilación de datos. Consulte <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> el período de gracia del servicio de ID</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Un solo archivo JavaScript de Analytics </p> </td> 
   <td colname="col2"> <p>Puede actualizar el archivo JavaScript para utilizar el servicio de ID de visitante sin un período de gracia. </p> </td> 
  </tr> 
 </tbody> 
</table>

## ¿Está utilizando métodos de recopilación de datos no compatibles?

Es posible que deba cambiar la manera en que realiza un seguimiento de los vínculos o bien dejar de utilizar Silverlight.

<table id="table_A72AEB92F48345DD83F136B9989F4EF9"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Método de recopilación de datos </th> 
   <th colname="col2" class="entry"> Acciones requeridas </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>JavaScript y/o Flash </p> </td> 
   <td colname="col2"> <p>Ninguno. El servicio de ID de <span class="keyword">Experience Cloud</span> es compatible con estos métodos de recopilación de datos. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Silverlight </p> </td> 
   <td colname="col2"> <p>Es necesario que migre de Silverlight si los visitantes pueden acceder a contenido de Silverlight y otras secciones de su sitio que utilizan el servicio de ID de <span class="keyword">Experience Cloud</span>. Silverlight no es compatible con el servicio de ID. </p> <p> Si realiza un seguimiento de un reproductor de vídeos basado en Silverlight, es probable que su proveedor pueda proporcionarle las API de JavaScript que puede usar en su lugar. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Etiquetas de imágenes cifradas </p> </td> 
   <td colname="col2"> <p>Actualice los enlaces cifrados para utilizar JavaScript. </p> </td> 
  </tr> 
 </tbody> 
</table>

