---
description: 'El servicio Experience Cloud ID ofrece un identificador universal y persistente que identifica a los visitantes en todas las soluciones de Experience Cloud. '
keywords: Servicio de ID
seo-description: El servicio de ID de Adobe Experience Cloud proporciona un ID universal y persistente que identifica a los visitantes en todas las soluciones de Experience Cloud. Puede reemplazar el código de generación de ID en servicios como Analytics, Audience Manager, Target y otras soluciones o funciones de Experience Cloud.
seo-title: Servicio Experience Cloud ID
title: Servicio Experience Cloud ID
uuid: b 68194 b 5-e 549-4 f 6 f-bfaf -7744926 aeaac
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Servicio Experience Cloud ID {#experience-cloud-id-service}

El servicio Experience Cloud ID (Servicio de ID) ofrece un identificador universal y persistente que identifica a los visitantes en todas las soluciones de Experience Cloud. Puede reemplazar el código de generación de ID en servicios como Analytics, Audience Manager, Target y otras soluciones o funciones de Experience Cloud.

<table id="table_5E612F746A704FE095B809A013EE977F" class="simpletable"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Primeros pasos</b> </p> <p> 
     <ul id="ul_D5EC6A54A03F4AB595B588116A7C1296"> 
      <li id="li_845F6DE25A1241439BCDCBC00459D7EB"> <a href="mcvid-introduction/mcvid-overview.md" format="dita" scope="local">Información general  </a> </li> 
      <li id="li_47F399E1D4AF4F08BD647DF01A423BA7"> <a href="mcvid-reference/mcvid-requirements.md" format="dita" scope="local"> Requisitos del servicio Experience Cloud ID </a> </li> 
      <li id="li_CBEEE79B45644F28A52B58DDF23DAD4F"> <a href="mcvid-implementation-guides/mcvid-standard.md#concept-89cd0199a9634fc48644f2d61e3d2445" format="dita" scope="local"> Implementación estándar con DTM </a> </li> 
     </ul> </p> <p><b>Bibliotecas JavaScript de Experience Cloud ID</b> </p> <p>JavaScript para el servicio Experience Cloud ID se encuentra aquí: <a href="https://github.com/Adobe-Marketing-Cloud/id-service/releases" format="https" scope="external">https://github.com/Adobe-Marketing-Cloud/id-service/releases</a> </p> <p> <b>Elementos nuevos o destacados</b> </p> <p> 
     <ul id="ul_B0A25B6827734D55BB1E20D12334AC21"> 
      <li id="li_A66924F4948F4A5ABA545A89A28A6F6A"><a href="mcvid-implementation-guides/opt-in-service/mcvid-optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> Servicio Opt-in</a> </li> 
      <li id="li_92D49CB788AD478EA74BCF5328CB9A14"> <a href="mcvid-library/mcvid-get-set/mcvid-getvisitorvalues.md#reference-b8c9e17c170c4291829a792df46ce279" format="dita" scope="local"> getVisitorValues </a> </li> 
      <li id="li_9E512C6DD15C46C3ABD06ACD60D97E4A"> <a href="mcvid-faq-intro/mcvid-faq-intro.md" format="dita" scope="local"> Preguntas frecuentes </a> </li> 
      <li id="li_B28082F3D075413D89E5AFB718657E17"> <a href="mcvid-library/mcvid-function-vars/mcvid-coopsafe.md#reference-7fbed36f38a048d1a5883c53d430ddf4" format="dita" scope="local"> isCoopSafe </a> </li> 
      <li id="li_7744A4898EA542B9BF009D2066810050"> <a href="mcvid-library/mcvid-function-vars/mcvid-idsyncontainerid.md#reference-5cfbed2240fa4def90f535f017a36015" format="dita" scope="local"> idSyncContainerID </a> </li> 
     </ul> </p> 
    <draft-comment> 
     <p> <b>Anuncios:</b> </p> 
     <p> <p>Importante: La compatibilidad con el servicio de ID para Internet Explorer 6, 7 y 8 está obsoleta y se suspenderá en una versión futura. </p> </p> 
    </draft-comment> </td> 
   <td colname="col2"> <p> <b>Notas de la versión</b> </p> <p><b>La versión 4.0</b> del 12 de febrero de 2019 incluye el servicio <a href="mcvid-implementation-guides/opt-in-service/mcvid-optin-overview.md#concept-f9b5db0d27a245fbadd3e19162319360" format="dita" scope="local"> de selección</a> utilizado para identificar si puede colocar una cookie en el dispositivo o el navegador de un usuario al visitar el sitio. </p> <p>La versión del 18 de enero de 2018 incluye la actualización de JavaScript 3.0.0 y las actualizaciones para los métodos de API. Consulte <a href="mcvid-library/mcvid-function-vars/mcvid-disableidsync.md#reference-589d6b489ac64eddb5a7ff758945e414" format="dita" scope="local"> Disableidsyncs</a> y <a href="mcvid-library/mcvid-function-vars/mcvid-disable-cookies.md#reference-2dd2d60d12f34f0b98bbb5606b3734cc" format="dita" scope="local"> disablethirdpartycookies</a>. </p> 
    <draft-comment> 
     <p>La versión de octubre de 2017 no incluye ningún cambio ni actualizaciones de código para el servicio de ID. El código de servicio de ID permanece sin cambios en la versión v 2.5. </p> 
    </draft-comment> 
    <draft-comment> 
     <p> La versión de septiembre de 2017 actualiza el código de servicio de ID a v 2.5. </p> 
    </draft-comment> <p> 
     <ul id="ul_4F06F170F214492780C7D25A069F799F"> 
      <li id="li_45A7CD556FE44F4DAB035C736A058F36"> Consulte las últimas <a href="https://marketing.adobe.com/resources/help/en_US/whatsnew/" format="https" scope="external">Notas de la versión de Experience Cloud</a> para ver las nuevas funciones y modificaciones. </li> 
      <li id="li_10CC4FBFEFC947CA9AD15F52D9715257">Consulte las <a href="https://marketing-stage.adobe.com/resources/help/en_US/whatsnew/c_legacy_releases.html" format="html" scope="external">notas de la versión anteriores</a> para ver versiones más antiguas. </li> 
     </ul> </p> <p> <b>Recursos de Experience Cloud</b> </p> <p> 
     <ul id="ul_E30EC96BDC624B5591F0470D430B7F41"> 
      <li id="li_F3A5CCFAE0F247CEB41A03CA8E03106B"> <a href="http://www.adobe.com/privacy.html" format="http" scope="external"> Centro de privacidad de Adobe</a> </li> 
      <li id="li_A54C1EB170EA4B8FA6A81B90AB0C39DD"> <a href="http://www.adobe.com/marketing-cloud.html" scope="external" format="http"> Adobe Experience Cloud</a> </li> 
      <li id="li_1938F7044F544481A6CC0F45CC22B80A"> <a href="http://helpx.adobe.com/learning.html?promoid=KAUDK" scope="external" format="http"> Formación y tutoriales de Adobe</a> </li> 
      <li id="li_C71459E0D1464C05B8B9387C43541F17"> <a href="https://marketing.adobe.com/resources/help/en_US/home/index.html" scope="external" format="https"> Página de inicio de documentación del producto</a> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

