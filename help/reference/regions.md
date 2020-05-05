---
description: La cookie AMCV contiene el Experience Cloud ID (MID) y un ID de región para los visitantes del sitio. Estos ID se almacenan como pares clave-valor. El ID mid user guarda el Experience Cloud ID del visitante. El ID aamlh region guarda el ID de región de los visitantes del sitio. Esta información se puede recuperar analizando la cookie de AMCV.
keywords: ID Service
seo-description: La cookie AMCV contiene el Experience Cloud ID (MID) y un ID de región para los visitantes del sitio. Estos ID se almacenan como pares clave-valor. El ID mid user guarda el Experience Cloud ID del visitante. El ID aamlh region guarda el ID de región de los visitantes del sitio. Esta información se puede recuperar analizando la cookie de AMCV.
seo-title: Obtención de ID de región y de usuario desde la cookie de AMCV o el servicio de ID
title: Obtención de ID de región y de usuario desde la cookie de AMCV o el servicio de ID
uuid: bdd9d001-f29f-4ff0-800b-8182243da218
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# Obtención de ID de región y de usuario desde la cookie de AMCV o el servicio de ID {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

La cookie AMCV contiene el Experience Cloud ID (MID) y un ID de región para los visitantes del sitio. Estos ID se almacenan como pares clave-valor. El ID mid:user guarda el Experience Cloud ID del visitante. El ID aamlh:region contiene el ID de región para los visitantes del sitio. Esta información se puede recuperar analizando la cookie de AMCV.

For more information, see [Get User IDs and Regions Through the Experience Cloud Identity Service](https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-mcid-ids.html).

Si es [!DNL Audience Manager] cliente de, puede obtener el ID de región a partir de la respuesta que envíe el servidor de recopilación de datos (DCS). See [Get User IDs and Regions from a DCS Response](https://docs.adobe.com/content/help/en/audience-manager/user-guide/api-and-sdk-code/dcs/dcs-apis/dcs-aam-ids.html).

También puede obtener el ID de región a través de un `GET` método que proporcione el servicio de ID. Consulte [Obtener ID de región (ubicación)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c)
