---
description: Si tiene varios archivos JavaScript que envían datos al mismo grupo de informes o si utiliza otras tecnologías en el sitio, como la medición de vídeo Flash, le recomendamos que configure un período de gracia.
keywords: Servicio de ID
seo-description: Si tiene varios archivos JavaScript que envían datos al mismo grupo de informes o si utiliza otras tecnologías en el sitio, como la medición de vídeo Flash, le recomendamos que configure un período de gracia.
seo-title: Período de gracia del servicio de ID
title: Período de gracia del servicio de ID
uuid: 10 a 7 db 7 d-de 32-4379-914 f-edaf 929 efa 32
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# Período de gracia del servicio de ID {#the-id-service-grace-period}

Si tiene varios archivos JavaScript que envían datos al mismo grupo de informes o si utiliza otras tecnologías en el sitio, como la medición de vídeo Flash, le recomendamos que configure un período de gracia.

Una vez que haya implementado el servicio de ID de [!DNL Experience Cloud], el servidor de recopilación de datos ya no asignará a los visitantes nuevos un ID de visitante de Analytics. Si hay secciones de su sitio que todavía no hayan implementado el servicio de ID de [!DNL Experience Cloud], cuando los visitantes accedan a ellas, el Experience Cloud ID no se reconocerá y se asignará un ID de visitante de Analytics heredado a los visitantes. De este modo, se pueden generar recuentos de visitas duplicados y una atribución incorrecta.

Por ejemplo, si la sección de soporte técnico de su sitio se administra en un CMS independiente, es posible que tenga un archivo JavaScript de Analytics distinto para esta sección. Si implementa el ID de visitante en el sitio principal antes de implementar el servicio de ID de visitante en el sitio de soporte técnico, los visitantes nuevos recibirán un ID de Analytics heredado cuando visiten la sección de soporte, y las visitas que abarquen las dos secciones del sitio se contabilizarán como visitas distintas.

La implementación del servicio de ID de [!DNL Experience Cloud] en sitios que utilicen varios archivos JavaScript u otras tecnologías (como Flash) puede producir problemas de coordinación, ya que será necesario habilitar el servicio de ID en todas las áreas del sitio al mismo tiempo. Si configura un período de gracia, el servicio de ID de [!DNL Experience Cloud] seguirá asignando un ID de visitante de Analytics a los nuevos visitantes, de manera que estos se puedan identificar de manera sistemática en las secciones del sitio que todavía no utilicen el servicio de ID.

>[!NOTE]
>
>La compatibilidad con período de gracia requiere la versión 1.3 o posterior del servicio [!DNL Experience Cloud] de ID.

## ¿Necesito un período de gracia? {#section-fd34c7ff697348a39f49258b7d39eb42}

Si tiene un solo archivo JavaScript de Analytics y no utiliza otras bibliotecas de AppMeasurement, no necesita un período de gracia. Puede realizar la actualización en el archivo JavaScript y se podrá identificar a los nuevos visitantes de forma consistente durante la visita mediante el Marketing Cloud ID.

Si tiene varios archivos JavaScript que envían datos al *mismo grupo de informes* o si utiliza otras tecnologías en el sitio, como la medición de vídeo Flash, le recomendamos que configure un período de gracia.

## ¿Cómo puedo habilitar un período de gracia? {#section-512d5cd8570e483cbdd8b04457a16ced}

Póngase en contacto con [el Servicio de atención al cliente](https://helpx.adobe.com/marketing-cloud/contact-support.html).
