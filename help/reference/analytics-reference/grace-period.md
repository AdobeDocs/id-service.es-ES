---
description: Si tiene varios archivos JavaScript que envían datos al mismo grupo de informes o si utiliza otras tecnologías en el sitio, como la medición de vídeo Flash, le recomendamos que configure un período de gracia.
keywords: Servicio de ID
seo-description: Si tiene varios archivos JavaScript que envían datos al mismo grupo de informes o si utiliza otras tecnologías en el sitio, como la medición de vídeo Flash, le recomendamos que configure un período de gracia.
seo-title: Período de gracia del servicio de ID
title: Período de gracia del servicio de ID
uuid: 10a7db7d-de32-4379-914f-edaf929efa32
exl-id: 83b4898c-8358-458b-a798-1e3c9633afe9
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '458'
ht-degree: 100%

---

# Período de gracia del servicio de ID {#the-id-service-grace-period}

Si tiene varios archivos JavaScript que envían datos al mismo grupo de informes o si utiliza otras tecnologías en el sitio, como la medición de vídeo Flash, le recomendamos que configure un período de gracia.

Una vez que haya implementado el [!DNL Experience Cloud] servicio de ID de, el servidor de recopilación de datos ya no asignará a los visitantes nuevos un ID de visitante de Analytics. Si hay secciones de su sitio que todavía no hayan implementado el servicio de ID de [!DNL Experience Cloud], cuando los visitantes accedan a ellas, el Experience Cloud ID no se reconocerá y se asignará un ID de visitante de Analytics heredado a los visitantes. Esto puede crear recuentos de visitas duplicados y una atribución incorrecta.

Por ejemplo: Si la sección de asistencia técnica de su sitio se administra en un CMS independiente, puede tener un archivo JavaScript de Analytics diferente para esta sección. Si implementa el ID de visitante en el sitio principal antes de implementar el servicio de ID de visitante en el sitio de asistencia, los nuevos visitantes recibirán un ID de Analytics heredado cuando visiten la sección de asistencia y las visitas que abarquen ambas secciones del sitio se registrarán como visitas diferentes.

La implementación del servicio de [!DNL Experience Cloud] ID de en sitios que utilicen varios archivos JavaScript u otras tecnologías (como Flash) puede producir problemas de coordinación, ya que será necesario habilitar el servicio de ID en todas las áreas del sitio al mismo tiempo. Si configura un período de gracia, el servicio de ID de [!DNL Experience Cloud] seguirá asignando un ID de visitante de Analytics a los nuevos visitantes, de manera que estos se puedan identificar de manera sistemática en las secciones del sitio que todavía no utilicen el servicio de ID.

>[!NOTE]
>
>Para utilizar el período de gracia se necesita la versión 1.3 o posterior del servicio de ID de [!DNL Experience Cloud].

## ¿Necesito un período de gracia? {#section-fd34c7ff697348a39f49258b7d39eb42}

Si tiene un solo archivo JavaScript de Analytics y no utiliza otras bibliotecas de AppMeasurement, no necesita ningún periodo de gracia. Puede realizar la actualización en el archivo JavaScript y se podrá identificar a los nuevos visitantes de forma constante durante la visita mediante el Experience Cloud ID.

Si tiene varios archivos JavaScript que envían datos al *mismo grupo de informes* o si utiliza otras tecnologías en el sitio, como la medición de vídeo Flash, le recomendamos que configure un periodo de gracia.

## ¿Cómo puedo habilitar un período de gracia?  {#section-512d5cd8570e483cbdd8b04457a16ced}

Póngase en contacto con el [Servicio de atención al cliente](https://helpx.adobe.com/es/marketing-cloud/contact-support.html).
