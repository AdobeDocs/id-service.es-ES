---
description: Lea esta sección para asegurarse de que está empleando las soluciones, los servicios y las versiones de código adecuados que requiere el servicio de identidad de Experience Cloud.
keywords: Servicio de ID
seo-description: Lea esta sección para asegurarse de que está empleando las soluciones, los servicios y las versiones de código adecuados que requiere el servicio de identidad de Experience Cloud.
seo-title: Requisitos del servicio de identidad de Experience Cloud
title: Requisitos del servicio de Experience Cloud ID
uuid: 608b1082-6e9e-4101-b6cb-60027950109b
translation-type: ht
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Requisitos del servicio de identidad de Experience Cloud {#requirements-for-the-experience-cloud-id-service}

Lea esta sección para asegurarse de que está empleando las soluciones, los servicios y las versiones de código adecuados que requiere el servicio de Experience Cloud ID.

## Los requisitos garantizan el éxito y la compatibilidad de la implementación {#section-15e54a9e9ad2443cb9dc950b4a78f1f1}

Una implementación correcta y compatible cumplirá (o sobrepasará) los requisitos en cuanto a código y seguirá las instrucciones tal cual se indican en la Ayuda de [!DNL Adobe]. Una implementación no compatible generará resultados no esperados e impedirá que el Servicio de atención al cliente y nuestros equipos de ingenieros puedan ayudarle a solucionar problemas con el servicio de ID.

<table id="table_2216C44AA66248DCAA13BF64BDF2D88A"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Tipo de implementación </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <a href="../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445" format="dita" scope="local"> Standard</a> </p> </td> 
   <td colname="col2"> <p>Para realizar una implementación estándar con Dynamic Tag Management (DTM), deberá hacer lo que sigue: </p> 
    <ul id="ul_59CDE179566844B494F3068FF6333809"> 
     <li id="li_CCCB6AFC08EE405F94C42216D3CE50AC"> Colocar el código de encabezado incrustado en la sección <span class="codeph">&lt;head&gt;</span> de la página. </li> 
     <li id="li_13962F2CB1764091A84863BE499675A2">Colocar el código de pie de página incrustado antes de la etiqueta de cierre <span class="codeph">&lt;/body&gt;</span>. </li> 
    </ul> <p>Una implementación estándar no resulta compatible cuando: </p> 
    <ul id="ul_3B62559317ED4C7AA548C3B8DBA281F7"> 
     <li id="li_1F16C6D412944197BEA56BC24730782C"> Se colocan cualquiera de estos códigos DTM incrustados en otra parte del código de la página o marcación. </li> 
     <li id="li_05615C01F3A947BBBD41046E68377224"> Se adjunta, agrega o carga código DTM con métodos asíncronos, métodos de llamada/rellamada o contenedores. </li> 
     <li id="li_B2137DFF627B473FA876580449026D2B">Se incluyen varias instancias de código incrustado en la misma página. </li> 
    </ul> <p>Consulte también <a href="https://marketing.adobe.com/resources/help/es_ES/dtm/?f=deployment.html" format="https" scope="external">Incrustar código y opciones de alojamiento</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <a href="../implementation-guides/implementation-guides.md#section-2c4f2db1f9704315a7cccab6d2e07113" format="dita" scope="local"> Implementaciones no estándar </a> </p> </td> 
   <td colname="col2"> <p>Si va a realizar implementaciones no estándar o manuales, deberá configurar el servicio de ID tal y como se describe en los procedimientos de esta guía. Como con las directrices para DTM más arriba, el hecho de colocar y cargar código erróneo hará que la implementación no resulte compatible. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Requisitos de Experience Cloud: ID de organización {#section-a02f537129a64ffbb690d5738d360c26}

Para emplear el servicio de ID, su empresa debe poder usar [!DNL Experience Cloud] y contar con un ID de organización. Consulte la lista siguiente si no está seguro sobre el estado de [!DNL Experience Cloud] de su empresa y necesita encontrar su ID de organización.

>[!IMPORTANT]
>
>El ID de organización distingue entre mayúsculas y minúsculas, y debe escribirse exactamente como se facilita.

<table id="table_6C74B676EB094C568D2439FDCC9A7830"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Estado de Experience Cloud </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Habilitada</b> </p> </td> 
   <td colname="col2"> <p>Si su empresa está habilitada para <span class="keyword">Experience Cloud</span> pero no tiene el ID de la organización, consulte <a href="https://marketing.adobe.com/resources/help/es_ES/mcloud/organizations.html" format="https" scope="external">ID de organización</a> (desplácese hacia abajo hasta la sección <i>Buscar el ID de su organización</i>). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>No estoy seguro</b> </p> </td> 
   <td colname="col2"> <p> Si no sabe si su empresa puede usar o no <span class="keyword">Experience Cloud</span>, pregunte a la persona que administre su cuenta de Adobe si sus empleados pueden iniciar sesión en <a href="https://marketing.adobe.com" format="https" scope="external">marketing.adobe.com</a> con un Adobe ID. Si es así, su empresa está habilitada y un administrador puede ver su ID de organización. Para buscar el ID de organización, consulte la sección "Página de administración" en <a href="https://marketing.adobe.com/resources/help/es_ES/mcloud/?f=admin_getting_started" format="https" scope="external">Administración de Experience Cloud</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>No habilitada</b> </p> </td> 
   <td colname="col2"> <p> Si su empresa no está habilitada para usar Experience Cloud, consulte <a href="https://marketing.adobe.com/resources/help/es_ES/mcloud/?f=core_services.html" format="https" scope="external">Servicios principales: Cómo activar las soluciones</a> para empezar. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Requisitos de Analytics: Recopilación de datos regionales (RDC) {#section-7d04bb013bc84a25bae3b148bc0ca25f}

Todos los servidores de seguimiento se han convertido a RDC, por lo que no es necesario cambiar el servidor de seguimiento de Analytics. [Más información…](https://docs.adobe.com/content/help/en/analytics/admin/data-collection/regional-data-collection/regional-data-collection.html)

## Bibliotecas de códigos y requisitos de la versión {#section-ad7542a4317d430fa79fc6b095beb84d}

En las siguientes secciones se enumeran las versiones de códigos mínimas que son necesarias para utilizar el servicio de ID de [!DNL Experience Cloud].

>[!TIP]
>
>Recomendamos utilizar las últimas versiones de código en lugar del mínimo requerido.

**JavaScript**

<table id="table_8E773F76DBCB4797A0C117080CA8707C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Solución de Experience Cloud </th> 
   <th colname="col3" class="entry"> Biblioteca de códigos </th> 
   <th colname="col4" class="entry"> Requisitos en cuanto a versiones </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b> <span class="keyword"> servicio de Experience Cloud ID</span></b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> VisitorAPI.js</span> </p> </td> 
   <td colname="col4"> <p>2.0 o posterior </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="2"> <p> <b><span class="keyword">Analytics </span></b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> AppMeasurement.js</span> </p> <p>Consulte <a href="https://marketing.adobe.com/resources/help/es_ES/sc/implement/?f=appmeasure_mjs.html" format="https" scope="external">AppMeasurement para JavaScript</a>. </p> </td> 
   <td colname="col4"> <p>1.6.4 o posterior </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> s_code.js</span> </p> </td> 
   <td colname="col4"> <p>H.27 </p> <p> <p>Nota:<span class="keyword"> Analytics</span> s_code versión H.27 ya no es compatible con la versión del servicio de ID 1.6.0. Actualice su código a la última versión de AppMeasurement. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p>Video Heartbeat </p> <p>Consulte <a href="https://marketing.adobe.com/resources/help/es_ES/sc/appmeasurement/hbvideo/index.html" format="https" scope="external">Video Heartbeat 2.x para JavaScript</a>. </p> </td> 
   <td colname="col4"> <p>2.0 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> <span class="keyword"> Audience Manager </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> dil.js</span> </p> <p> Consulte <a href="https://marketing.adobe.com/resources/help/en_US/aam/?f=c_dil.html" format="https" scope="external">Biblioteca de integración de datos</a> (DIL). </p> </td> 
   <td colname="col4"> <p>5.0 </p> <p> 
     <draft-comment>
       actualizado desde la versión 4.9 
     </draft-comment> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="1"> <p> <b> <span class="keyword"> Target </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> mbox.js</span> </p> <p>Consulte <a href="https://marketing.adobe.com/resources/help/es_ES/target/ov/?f=c_mbox_technical.html" format="https" scope="external">Código mbox</a>. </p> </td> 
   <td colname="col4"> <p>61 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> at.js</span> </p> <p>Consulte <a href="https://marketing.adobe.com/resources/help/es_ES/target/ov2/c_target-atjs-implementation.html" format="https" scope="external">Implementación de at.js</a>. </p> </td> 
   <td colname="col4"> <p>0.9.1 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Requisitos de SDK para Android e iOS {#section-73b2446fba8e463888642c7d7dfd94f1}

El servicio de ID requiere como mínimo las versiones de SDK que se indican a continuación.

* Android: 4.11.0
* iOS: 4.11.0

>[!TIP]
>
>Recomendamos utilizar las últimas versiones de código en lugar del mínimo requerido.

Su código SDK debe haber sido habilitado para usar el servicio de ID. Habilite y descargue el último código SDK disponible para cada aplicación desde su cuenta de [Adobe Mobile Services](https://mobilemarketing.adobe.com/). Consulte también:

* [Configuración de las opciones del servicio de ID para el SDK de visitantes](https://marketing.adobe.com/resources/help/es_ES/mobile/t_config_visitor.html)
* [Métodos de SDK para Android](https://marketing.adobe.com/resources/help/es_ES/mobile/android/c_marketing_cloud.html)
* [Métodos de SDK para iOS](https://marketing.adobe.com/resources/help/es_ES/mobile/ios/marketing_cloud.html)

>[!MORE_LIKE_THIS]
>
>* [Biblioteca de códigos](../library/library.md#concept-ff27497375644a898d47984aefb21c97)

