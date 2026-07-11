---
description: Lea esta sección para asegurarse de que está empleando las soluciones, los servicios y las versiones de código adecuados que requiere el servicio de ID de visitante.
keywords: Servicio de ID de visitante
title: Requisitos del servicio de ID de visitante de Adobe
exl-id: ebeac4c7-b36c-4a4e-9378-351fac5baf53
TQID: https://experienceleague.adobe.com/yOoLEIKihVSpDLeZsplTZzg-toOENKlBzsQt2G2YcKk
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: df401a2a-327d-468c-a5e4-b7b7ccd071a0
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 727
ht-degree: 39%

---

# Requisitos del servicio de ID de visitante de Adobe {#requirements-for-the-experience-cloud-id-service}

Lea esta sección para asegurarse de que está empleando las soluciones, los servicios y las versiones de código adecuados que requiere el servicio de ID de visitante.

## Los requisitos garantizan el éxito y la compatibilidad de la implementación {#section-15e54a9e9ad2443cb9dc950b4a78f1f1}

Una implementación correcta y compatible cumple (o supera) los requisitos de código y sigue las instrucciones tal y como se muestran en la ayuda de Adobe. Una implementación no admitida generará resultados inesperados e impedirá que el Servicio de atención al cliente y nuestros equipos de ingeniería colaboren con los esfuerzos para solucionar o resolver sus problemas con el servicio de ID de visitante.

### Implementaciones estándar

Consulte [tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=es) en la recopilación de datos de Adobe Experience Platform para su implementación estándar.

### Implementaciones no estándar

Para implementaciones no estándar o manuales, debe configurar el servicio de ID de visitante como se describe en los procedimientos de esta guía. Al igual que con las directrices de implementación estándar anteriores, la colocación y carga incorrectas del código creará una implementación no compatible.

## Requisitos empresariales de CX: ID de organización de IMS {#section-a02f537129a64ffbb690d5738d360c26}

Para utilizar el servicio de ID de visitante, su empresa debe estar habilitada para CX Enterprise y tener un ID de organización de IMS. Consulte la siguiente lista si no está seguro del estado empresarial de CX de su empresa y necesita encontrar su ID de organización de IMS.

>[!IMPORTANT]
>
>El ID de organización de IMS distingue entre mayúsculas y minúsculas y debe escribirse exactamente como se facilita.

<table id="table_6C74B676EB094C568D2439FDCC9A7830"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Estado de CX Enterprise </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Habilitado</b> </p> </td> 
   <td colname="col2"> <p>Si su empresa está habilitada para CX Enterprise pero usted no tiene su identificador de organización de IMS, consulte <a href="https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html?lang=es" format="https" scope="external"> identificadores de organización</a> (desplácese hacia abajo hasta la sección <i>Buscar su identificador de organización</i>). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>No estoy seguro</b> </p> </td> 
   <td colname="col2"> <p> Si no sabe el estado de CX Enterprise de su empresa, pregunte a la persona que administre su cuenta de Adobe si los miembros de su empresa pueden iniciar sesión en <a href="https://experiencecloud.adobe.com" format="https" scope="external"> marketing.adobe.com</a> con un Adobe ID. Si es así, está habilitado y un administrador puede ver su ID de organización de IMS. Para encontrar el identificador de organización de IMS, consulte la sección "Página de administración" en <a href="https://experienceleague.adobe.com/docs/core-services/interface/experience-cloud.html?lang=es" format="https" scope="external"> CX Enterprise Administration</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>No habilitada</b> </p> </td> 
   <td colname="col2"> <p> Si su empresa no está habilitada para CX Enterprise, consulte <a href="https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html?lang=es" format="https" scope="external"> Servicios principales: Cómo habilitar las soluciones</a> para comenzar. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Requisitos de Analytics: Recopilación de datos regionales (RDC) {#section-7d04bb013bc84a25bae3b148bc0ca25f}

Todos los servidores de seguimiento se han convertido a RDC, por lo que no es necesario cambiar el servidor de seguimiento de Analytics. [Más información...](https://experienceleague.adobe.com/docs/analytics/technotes/rdc/regional-data-collection.html?lang=es)

## Bibliotecas de códigos y requisitos de la versión {#section-ad7542a4317d430fa79fc6b095beb84d}

En las secciones siguientes se enumeran las versiones de código mínimas que son necesarias para utilizar el servicio de ID de visitante.

>[!TIP]
>
>Recomendamos utilizar las últimas versiones de código en lugar del mínimo requerido.

**JavaScript**

<table id="table_8E773F76DBCB4797A0C117080CA8707C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Solución empresarial de CX </th> 
   <th colname="col3" class="entry"> Biblioteca de códigos </th> 
   <th colname="col4" class="entry"> Requisitos de versión </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Servicio de ID de visitante</b> </p> </td> 
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
   <td colname="col4"> <p>H.27 </p> <p> <p>Nota: <span class="keyword"> Analytics</span> s_code versión H.27 ya no es compatible con la versión 1.6.0 del servicio de ID de visitante. Actualice el código a la última versión de AppMeasurement. </p> </p> </td> 
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
   <td colname="col3"> <p> <span class="codeph"> mbox.js</span> </p> <p>Consulte <a href="https://experienceleague.adobe.com/en/docs/target-dev/developer/client-side/at-js-implementation/at-js/overview" format="https" scope="external">Código mbox</a>. </p> </td> 
   <td colname="col4"> <p>61 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col3"> <p> <span class="codeph"> at.js</span> </p> <p>Consulte <a href="https://experienceleague.adobe.com/en/docs/target-dev/developer/client-side/at-js-implementation/at-js/how-atjs-works" format="https" scope="external">Implementación de at.js</a>. </p> </td> 
   <td colname="col4"> <p>0.9.1 </p> </td> 
  </tr> 
 </tbody> 
</table>

## Requisitos de SDK para Android e iOS {#section-73b2446fba8e463888642c7d7dfd94f1}

Como mínimo, el servicio de ID de visitante requiere las versiones de SDK que se indican a continuación.

* Android: 4.11.0
* iOS: 4.11.0

>[!TIP]
>
>Recomendamos utilizar las últimas versiones de código en lugar del mínimo requerido.

Su código SDK debe estar habilitado para el servicio de ID de visitante. Habilite y descargue el último código SDK disponible para cada aplicación desde su cuenta de [Adobe Mobile Services](https://mobilemarketing.adobe.com/). Consulte también:

* [Configuración de las opciones del SDK de servicio de ID de visitante](https://experienceleague.adobe.com/docs/mobile-services/using/manage-app-settings-ug/configuring-app/t-config-visitor.html?lang=es)
* [Métodos del SDK para Android](https://experienceleague.adobe.com/docs/mobile-services/android/experience-cloud-android/c-marketing-cloud.html?lang=es)
* [Métodos SDK para iOS](https://experienceleague.adobe.com/docs/mobile-services/ios/exp-cloud-ios/marketing-cloud.html?lang=es)

>[!MORELIKETHIS]
>
>* [Biblioteca de códigos](../library/library.md#concept-ff27497375644a898d47984aefb21c97)
