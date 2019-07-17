---
description: Información general sobre cómo funciona el servicio de identidad de Experience Cloud con el ID de Analytics heredado.
keywords: Servicio de ID
seo-description: Información general sobre cómo funciona el servicio de identidad de Experience Cloud con el ID de Analytics heredado.
seo-title: Solicitudes de ID de Analytics y Experience Cloud ID
title: Solicitudes de ID de Analytics y Experience Cloud ID
uuid: 28beed16-7ef9-4824-8e82-853930756eca
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Solicitudes de ID de Analytics y Experience Cloud ID{#analytics-and-experience-cloud-id-requests}

Información general sobre cómo funciona el servicio de identidad de Experience Cloud con el ID de Analytics heredado.

## Resumen {#section-64d8523ff7634cb987d0c6480f587dd3}

Históricamente, el servicio de identidad de Experience Cloud se ha integrado correctamente en Adobe Analytics. Sigue formando parte integral de Analytics, pero ahora realiza funciones importantes para otras soluciones y características de [!DNL Experience Cloud]. Because of this historical legacy, checking for or writing an Analytics ID works a little differently than with the generic process described in [How the Experience Cloud Identity Service Requests and Sets IDs...](../../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a). Para obtener más información sobre el orden de las operaciones para comprobar el ID, consulte [Configuración de Analytics y Experience Cloud ID](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6).

## La cookie AMCV no se establece en el navegador {#section-cccf10cd775e4a95a7e98d3c3c0ff9a9}

Si la cookie [!DNL Experience Cloud] (AMCV) no está presente, una llamada al servicio de ID a [!DNL Adobe] genera una respuesta que varía según la presencia o ausencia de un ID de Analytics heredado. El ID de [!DNL Analytics] heredado se almacena en la [cookie s_vi](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html). La tabla siguiente describe cómo se escriben los ID en la cookie AMCV en función del estado de la cookie s_vi.

<table id="table_DC85FECE26DD424E841BA1059AF1E57F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Estado de la cookie s_vi </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b> La cookie s_vi no está establecida</b> </p> </td> 
   <td colname="col2"> <p>El servicio de ID asigna a los visitantes un <span class="keyword">Experience Cloud</span> (MID). El MID identifica a sus visitantes en <span class="keyword">Analytics</span> y otras soluciones de <span class="keyword">Experience Cloud</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>La cookie s_vi está establecida</b> </p> </td> 
   <td colname="col2"> <p>Cuando un visitante del sitio con una cookie s_ vi encuentra primero el servicio de identidad de Experience Cloud, este servicio: </p> 
    <ul id="ul_BE584810280D4874AF802A9247011787"> 
     <li id="li_AA395B09A3174AF78F3EC10053E2E4F5">Escribe el ID de <span class="keyword">Analytics</span> guardado en la cookie s_vi en la cookie AMCV. Este se escribe como el ID de <span class="keyword">Analytics</span> (AID). Esta acción <i>no</i> afecta a sus recuentos de visitantes. <span class="keyword"> Analytics</span> continuará identificando a los usuarios con sus ID heredados. </li> 
     <li id="li_8735DE21FEA542BA8024109B8FE1E2ED">Escribe el MID en la cookie AMCV. El MID identifica a los usuarios entre las distintas soluciones. </li> 
    </ul> <p> <p>Nota: Con un <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local">período de gracia</a>, la respuesta del centro de datos incluye siempre un ID heredado que se almacena en la cookie s_vi. Durante el período de gracia, el ID heredado se escribe en la cookie AMCV como el valor AID. </p> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>El valor FID heredado de los usuarios identificados por la cookie s_fid no se migrará a la cookie AMCV. Con una cookie s_fid, los usuarios se migrarán como si no hubiera una cookie s_vi presente (véase más arriba) y aparecen como visitantes nuevos para su sitio. Consulte [Cookies de Analytics](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html) para obtener más información.

## La cookie AMCV se establece en el explorador {#section-01c088fc565c4b24ba1722c7cc240310}

Si la cookie AMCV está presente, empleará el MID como el identificador de [!DNL Analytics] si no hay ningún valor de ID de [!DNL Analytics]Analytics heredado en la cookie.
