---
description: La cookie AMCV contiene el Experience Cloud ID (MID) y un ID de región para los visitantes del sitio. Estos ID se almacenan como pares clave-valor. El ID de usuario medio contiene el ID de Experience Cloud del visitante. El ID de región aamlh contiene el ID de región de los visitantes del sitio. Esta información se puede recuperar analizando la cookie de AMCV.
keywords: Servicio de ID
seo-description: La cookie AMCV contiene el Experience Cloud ID (MID) y un ID de región para los visitantes del sitio. Estos ID se almacenan como pares clave-valor. El ID de usuario medio contiene el ID de Experience Cloud del visitante. El ID de región aamlh contiene el ID de región de los visitantes del sitio. Esta información se puede recuperar analizando la cookie de AMCV.
seo-title: Obtención de ID de región y de usuario desde la cookie de AMCV o el servicio de ID
title: Obtención de ID de región y de usuario desde la cookie de AMCV o el servicio de ID
uuid: bdd 9 d 001-f 29 f -4 ff 0-800 b -8182243 da 218
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Obtención de ID de región y de usuario desde la cookie de AMCV o el servicio de ID {#get-region-and-user-ids-from-the-amcv-cookie-or-the-id-service}

La cookie AMCV contiene el Experience Cloud ID (MID) y un ID de región para los visitantes del sitio. Estos ID se almacenan como pares clave-valor. El ID mid:user guarda el Experience Cloud ID del visitante. El ID aamlh:region guarda el ID de región de los visitantes del sitio. Esta información se puede recuperar analizando la cookie de AMCV.

Para obtener más información, consulte [Obtención de ID de usuario y regiones mediante el servicio de identidad de la plataforma de Experience Platform](https://marketing.adobe.com/resources/help/en_US/aam/dcs-mcid-ids.html).

Si es cliente de [!DNL Audience Manager], puede obtener el ID de región a partir de la respuesta que envíe el servidor de recopilación de datos (DCS). Consulte [Obtención de ID y regiones de usuario a partir de una respuesta de DCS](https://marketing.adobe.com/resources/help/en_US/aam/dcs-aam-ids.html).

También puede obtener el ID de región a través de un método `GET` que proporcione el servicio de ID. Consulte [Obtención de ID de región (indicio de ubicación)](../library/get-set/getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c).
