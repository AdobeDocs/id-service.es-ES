---
description: 'El servicio de identidad de Experience Cloud ofrece un identificador universal y persistente que identifica a los visitantes en todas las soluciones de Experience Cloud. '
keywords: ID Service
seo-description: El servicio de Adobe Experience Cloud ID (Servicio de ID) ofrece un identificador universal y persistente que identifica a los visitantes en todas las soluciones de Experience Cloud. Puede reemplazar el código de generación de ID en servicios como Analytics, Audience Manager, Target y otras soluciones o funciones de Experience Cloud.
seo-title: Servicio de Experience Cloud ID
title: Servicio de Experience Cloud ID
uuid: b68194b5-e549-4f6f-bfaf-7744926aeaac
translation-type: ht
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3
workflow-type: ht
source-wordcount: '322'
ht-degree: 100%

---


# Servicio de Adobe Experience Cloud ID {#experience-cloud-id-service}

El servicio de Adobe Experience Cloud ID (Servicio de ID) ofrece un identificador universal y persistente que identifica a los visitantes en todas las soluciones de Experience Cloud. Puede reemplazar el código de generación de ID en servicios como Analytics, Audience Manager, Target y otras soluciones o funciones de Experience Cloud.

<table id="table_5E612F746A704FE095B809A013EE977F" class="simpletable"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Primeros pasos</b> </p> <p> 
     <ul id="ul_D5EC6A54A03F4AB595B588116A7C1296"> 
      <li id="li_845F6DE25A1241439BCDCBC00459D7EB"> <a href="introduction/overview.md" format="dita" scope="local">Información general </a> </li> 
      <li id="li_47F399E1D4AF4F08BD647DF01A423BA7"> <a href="reference/requirements.md" format="dita" scope="local"> Requisitos del servicio de identidad de Experience Cloud</a> </li> 
      <li id="li_CBEEE79B45644F28A52B58DDF23DAD4F"> <a href="implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445" format="dita" scope="local"> Implementación estándar con DTM </a> </li> 
     </ul> </p> <p><b>Bibliotecas JavaScript de Experience Cloud ID</b> </p> <p>El JavaScript para el servicio de identidad de Experience Cloud se encuentra aquí: <a href="https://github.com/Adobe-Marketing-Cloud/id-service/releases" format="https" scope="external">https://github.com/Adobe-Marketing-Cloud/id-service/releases</a> </p> <p> <b>Elementos nuevos o destacados</b> </p> <p> 
     <ul id="ul_B0A25B6827734D55BB1E20D12334AC21"> 
      <li id="li_A66924F4948F4A5ABA545A89A28A6F6A"><a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> Servicio Opt-in</a> </li> 
      <li id="li_92D49CB788AD478EA74BCF5328CB9A14"> <a href="library/get-set/getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues </a> </li> 
      <li id="li_9E512C6DD15C46C3ABD06ACD60D97E4A"> <a href="faq-intro/faq-intro.md" format="dita" scope="local"> Preguntas frecuentes </a> </li> 
      <li id="li_B28082F3D075413D89E5AFB718657E17"> <a href="library/function-vars/coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local"> isCoopSafe </a> </li> 
      <li id="li_7744A4898EA542B9BF009D2066810050"> <a href="library/function-vars/idsyncontainerid.md#reference-5cfbed2240fa4def90f535f017a36015" format="dita" scope="local"> idSyncContainerID </a> </li> 
     </ul> </p> 
    <draft-comment> 
     <p> <b>Anuncios:</b> </p> 
     <p> <p>Importante: El servicio de asistencia de ID para Internet Explorer 6, 7 y 8 está obsoleto y dejará de ofrecerse en futuras versiones. </p> </p> 
    </draft-comment> </td> 
   <td colname="col2"> <p> <b>Notas de la versión</b> </p> <p><b>La versión 4.4</b> del 17 de julio de 2019 incluye compatibilidad con el <a href="reference/hashing-support.md" format="dita" scope="local"> algoritmo hash SHA -256</a> que permite pasar ID de clientes o direcciones de correo electrónico y transferir ID hash.</p><p><b>La versión 4.0</b> del 12 de febrero de 2019 incluye el servicio <a href="implementation-guides/opt-in-service/optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local">Opt-in</a> utilizado para identificar si puede colocar una cookie en el dispositivo o el navegador de un usuario al visitar el sitio. </p> <p> 
     <ul id="ul_4F06F170F214492780C7D25A069F799F"> 
      <li id="li_45A7CD556FE44F4DAB035C736A058F36"> Consulte las últimas <a href="https://docs.adobe.com/content/help/es-ES/release-notes/experience-cloud/current.html" format="https" scope="external">Notas de la versión de Experience Cloud</a> para ver las nuevas funciones y modificaciones. </li> 
      <li id="li_10CC4FBFEFC947CA9AD15F52D9715257">Consulte las <a href="https://docs.adobe.com/content/help/es-ES/release-notes/experience-cloud/current.html" format="html" scope="external">notas de la versión anteriores</a> para ver versiones más antiguas. </li> 
     </ul> </p> <p> <b>Recursos de Experience Cloud</b> </p> <p> 
     <ul id="ul_E30EC96BDC624B5591F0470D430B7F41"> 
      <li id="li_F3A5CCFAE0F247CEB41A03CA8E03106B"> <a href="http://www.adobe.com/es/privacy.html" format="http" scope="external"> Centro de privacidad de Adobe</a> </li> 
      <li id="li_A54C1EB170EA4B8FA6A81B90AB0C39DD"> <a href="https://docs.adobe.com/content/help/es-ES/experience-cloud/user-guides/home.html" scope="external" format="http"> Adobe Experience Cloud</a> </li> 
      <li id="li_1938F7044F544481A6CC0F45CC22B80A"> <a href="http://helpx.adobe.com/es/learning.html?promoid=KAUDK" scope="external" format="http"> Formación y tutoriales de Adobe</a> </li> 
      <li id="li_C71459E0D1464C05B8B9387C43541F17"> <a href="https://helpx.adobe.com/es/support/experience-cloud.html" scope="external" format="https"> Página de inicio de documentación del producto</a> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

