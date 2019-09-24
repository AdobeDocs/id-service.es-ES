---
description: La cookie AMCV contiene el Experience Cloud ID (MID) y un ID de región para los visitantes del sitio. Estos ID se almacenan como pares clave-valor. El ID mid user guarda el Experience Cloud ID del visitante. El ID aamlh region guarda el ID de región de los visitantes del sitio. Esta información se puede recuperar analizando la cookie de AMCV.
keywords: Servicio de ID
seo-description: La cookie AMCV contiene el Experience Cloud ID (MID) y un ID de región para los visitantes del sitio. Estos ID se almacenan como pares clave-valor. El ID mid user guarda el Experience Cloud ID del visitante. El ID aamlh region guarda el ID de región de los visitantes del sitio. Esta información se puede recuperar analizando la cookie de AMCV.
seo-title: Obtención de ID de región y de usuario desde la cookie de AMCV o el servicio de ID
title: Obtención de ID de región y de usuario desde la cookie de AMCV o el servicio de ID
uuid: bdd9d001-f29f-4ff0-800b-8182243da218
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Obtención de ID de región y de usuario desde la cookie de AMCV o el servicio de ID {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

La cookie AMCV contiene el Experience Cloud ID (MID) y un ID de región para los visitantes del sitio. Estos ID se almacenan como pares clave-valor. El ID mid:user guarda el Experience Cloud ID del visitante. El ID aamlh:region guarda el ID de región de los visitantes del sitio. Esta información se puede recuperar analizando la cookie de AMCV.

For more information, see [Get User IDs and Regions Through the Experience Cloud Identity Service](https://marketing.adobe.com/resources/help/en_US/aam/dcs-mcid-ids.html).

Si es [!DNL Audience Manager] cliente de, puede obtener el ID de región a partir de la respuesta que envíe el servidor de recopilación de datos (DCS). Consulte [Obtención de ID y regiones de usuario a partir de una respuesta de DCS](https://marketing.adobe.com/resources/help/en_US/aam/dcs-aam-ids.html).

También puede obtener el ID de región a través de un `GET` método que proporcione el servicio de ID. Consulte [Obtener ID de región (ubicación)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c)
