---
description: Lea esta sección para asegurarse de que está empleando las soluciones, los servicios y las versiones de código adecuados que requiere el servicio de Experience Cloud ID.
keywords: Servicio de ID
title: Requisitos del servicio de Experience Cloud ID
exl-id: ebeac4c7-b36c-4a4e-9378-351fac5baf53
source-git-commit: 00ebcaa16ec6b432b480d96fbf79b6a745515b1b
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 96%

---

# Requisitos del servicio de Experience Cloud ID {#requirements-for-the-experience-cloud-id-service}

Lea esta sección para asegurarse de que está empleando las soluciones, los servicios y las versiones de código adecuados que requiere el servicio de Experience Cloud ID.

## Los requisitos garantizan el éxito y la compatibilidad de la implementación {#section-15e54a9e9ad2443cb9dc950b4a78f1f1}

Una implementación correcta y compatible cumplirá (o sobrepasará) los requisitos en cuanto a código y seguirá las instrucciones tal cual se indican en la Ayuda de [!DNL Adobe]. Una implementación no admitida generará resultados inesperados e impedirá que el Servicio de atención al cliente y nuestros equipos de ingeniería colaboren con los esfuerzos para solucionar o resolver sus problemas con el servicio de ID.

### Implementaciones estándar

Consulte las [etiquetas de Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=es) para su implementación estándar.

### Implementaciones no estándar

Para implementaciones no estándar o manuales, debe configurar el servicio de ID tal como se describe en los procedimientos de esta guía. Al igual que con las directrices de DTM anteriores, la colocación y carga incorrectas del código creará una implementación no compatible.

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
   <td colname="col1"> <p> <b>Habilitado</b> </p> </td> 
   <td colname="col2"> <p>Si su empresa está habilitada para <span class="keyword">Experience Cloud</span> pero no tiene el ID de la organización, consulte <a href="https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html?lang=es" format="https" scope="external">ID de organización</a> (desplácese hacia abajo hasta la sección <i>Buscar el ID de su organización</i>). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>No estoy seguro</b> </p> </td> 
   <td colname="col2"> <p> Si no sabe si su empresa puede usar o no <span class="keyword">Experience Cloud</span>, pregunte a la persona que administre su cuenta de Adobe si sus empleados pueden iniciar sesión en <a href="https://experiencecloud.adobe.com" format="https" scope="external">marketing.adobe.com</a> con un Adobe ID. Si es así, su empresa está habilitada y un administrador puede ver su ID de organización. Para buscar el ID de organización, consulte la sección "Página de administración" en <a href="https://experienceleague.adobe.com/docs/core-services/interface/experience-cloud.html?lang=es" format="https" scope="external">Administración de Experience Cloud</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>No habilitada</b> </p> </td> 
   <td colname="col2"> <p> Si su empresa no está habilitada para usar Experience Cloud, consulte <a href="https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html?lang=es" format="https" scope="external">Servicios principales: Cómo activar las soluciones</a> para empezar. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Requisitos de Analytics: Recopilación de datos regionales (RDC) {#section-7d04bb013bc84a25bae3b148bc0ca25f}

Todos los servidores de seguimiento se han convertido a RDC, por lo que no es necesario cambiar el servidor de seguimiento de Analytics. [Más información...](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html?lang=es)

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
   <th colname="col4" class="entry"> Requisitos de versión </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b> <span class="keyword"> servicio de</span> Experience Cloud ID</b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> VisitorAPI.js</span> </p> </td> 
   <td colname="col4"> <p>2.0 o posterior </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="2"> <p> <b> <span class="keyword">Analytics </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> AppMeasurement.js</span> </p> <p>Consulte <a href="https://experienceleague.adobe.com/docs/analytics/implementation/js/overview.html?lang=es" format="https" scope="external">AppMeasurement para JavaScript</a>. </p> </td> 
   <td colname="col4"> <p>1.6.4 o posterior </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> s_code.js</span> </p> </td> 
   <td colname="col4"> <p>H.27 </p> <p> <p>Nota:<span class="keyword"> Analytics</span> s_code versión H.27 ya no es compatible con la versión del servicio de ID 1.6.0. Actualice su código a la última versión de AppMeasurement. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p>Video Heartbeat </p> <p>Consulte <a href="https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=es" format="https" scope="external">Video Heartbeat 2.x para JavaScript</a>. </p> </td> 
   <td colname="col4"> <p>2.0 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b> <span class="keyword"> Audience Manager </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> dil.js</span> </p> <p> Consulte <a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/dil-api/dil-overview.html?lang=es" format="https" scope="external">Biblioteca de integración de datos</a> (DIL). </p> </td> 
   <td colname="col4"> <p>5.0 </p></td> 
  </tr> 
  <tr> 
   <td colname="col1" morerows="1"> <p> <b> <span class="keyword"> Target </span> </b> </p> </td> 
   <td colname="col3"> <p> <span class="codeph"> mbox.js</span> </p> <p>Consulte <a href="https://experienceleague.adobe.com/docs/target-dev/developer/client-side/at-js-implementation/overview.html?lang=en" format="https" scope="external">Código mbox</a>. </p> </td> 
   <td colname="col4"> <p>61 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> at.js</span> </p> <p>Consulte <a href="https://experienceleague.adobe.com/docs/target-dev/developer/client-side/at-js-implementation/at-js/how-atjs-works.html?lang=en" format="https" scope="external">Implementación de at.js</a>. </p> </td> 
   <td colname="col4"> <p>0.9.1 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Requisitos de SDK para Android e iOS {#section-73b2446fba8e463888642c7d7dfd94f1}

Como mínimo, el servicio de ID requiere las versiones del SDK que se indican a continuación.

* Android: 4.11.0
* iOS: 4.11.0

>[!TIP]
>
>Recomendamos utilizar las últimas versiones de código en lugar del mínimo requerido.

Su código SDK debe haber sido habilitado para usar el servicio de ID. Habilite y descargue el último código SDK disponible para cada aplicación desde su cuenta de [Adobe Mobile Services](https://mobilemarketing.adobe.com/). Consulte también:

* [Configuración de las opciones del SDK de servicio de ID de visitante](https://experienceleague.adobe.com/docs/mobile-services/using/manage-app-settings-ug/configuring-app/t-config-visitor.html?lang=es)
* [Métodos del SDK para Android](https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/c-marketing-cloud.html?lang=es)
* [Métodos SDK para iOS](https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/marketing-cloud.html?lang=es)

>[!MORELIKETHIS]
>
>* [Biblioteca de códigos](../library/library.md#concept-ff27497375644a898d47984aefb21c97)

