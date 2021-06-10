---
description: La cookie AMCV contiene el Experience Cloud ID (MID) y un ID de región para los visitantes del sitio. Estos ID se almacenan como pares clave-valor. El ID mid user guarda el Experience Cloud ID del visitante. El ID aamlh region guarda el ID de región de los visitantes del sitio. Esta información se puede recuperar analizando la cookie de AMCV.
keywords: Servicio de ID
title: Obtención de ID de región y de usuario desde la cookie de AMCV o el servicio de ID
exl-id: 986e761e-4bc7-4511-86b7-7d13a7761a2b
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 91%

---

# Obtención de ID de región y de usuario desde la cookie de AMCV o el servicio de ID {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

La cookie AMCV contiene el Experience Cloud ID (MID) y un ID de región para los visitantes del sitio. Estos ID se almacenan como pares clave-valor. El ID mid:user guarda el Experience Cloud ID del visitante. El ID aamlh:region guarda el ID de región de los visitantes del sitio. Esta información se puede recuperar analizando la cookie de AMCV.

Para obtener más información, consulte [Obtención de ID de usuario y regiones mediante el servicio de identidad de Experience Cloud](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html).

Si es [!DNL Audience Manager] cliente de, puede obtener el ID de región a partir de la respuesta que envíe el servidor de recopilación de datos (DCS). Consulte [Obtención de ID de usuario y regiones desde una respuesta de DCS](https://experienceleague.adobe.com/docs/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html).

También puede obtener el ID de región a través de un `GET` método que proporcione el servicio de ID. Consulte [Obtener ID de región (ubicación)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c)
