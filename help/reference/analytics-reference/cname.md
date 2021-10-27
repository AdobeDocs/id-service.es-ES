---
description: Si tiene un sitio de entrada principal en el que se puede identificar a los clientes antes de que visiten otros dominios, un registro CNAME puede habilitar el seguimiento entre dominios en los exploradores que no acepten cookies de terceros (como Safari).
keywords: orden de operaciones; servicio de ID
title: Información general sobre la implementación de CNAME
exl-id: f95dda3c-7bb2-4c7d-a25a-a4d20b58fe27
source-git-commit: 61f9f1888430ff0fdbb90a8cf6561bf23d204a45
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 45%

---

# Información general sobre la implementación de CNAME{#cname-implementation-overview}

Las implementaciones de CNAME le permiten personalizar el dominio de colección que utiliza Adobe para que coincida con su propio dominio. Estos dominios también se denominan dominios de colección de origen. Estas implementaciones permiten al Adobe establecer cookies de origen en el servidor en lugar de en el lado del cliente mediante JavaScript. En el pasado, estas cookies de origen del lado del servidor no estaban sujetas a los límites impuestos por la directiva de prevención inteligente del seguimiento (ITP) de Apple. Sin embargo, en noviembre de 2020, [!DNL Apple] actualizó sus directivas para que estas limitaciones también se aplicaran a las cookies configuradas mediante CNAME. Actualmente, ambas cookies configuradas en el servidor a través de CNAME y las cookies configuradas en el lado del cliente a través de Javascript están limitadas a una caducidad de siete o 24 horas en ITP. Para obtener más información sobre la directiva ITP, consulte este [!DNL Apple] documento [sobre la prevención de seguimiento](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp).

Aunque la implementación de CNAME no proporciona ningún beneficio en términos de duración de las cookies, puede haber otros beneficios. Estos beneficios incluyen bloqueadores de anuncios y exploradores menos comunes que impiden que se envíen datos a dominios que clasifican como rastreadores. En estos casos, el uso de un CNAME puede impedir que la recopilación de datos se interrumpa para los usuarios que utilizan estas herramientas.

Además, las implementaciones CNAME le permiten especificar **[!UICONTROL Elegir tipo de RDC personalizado]** que controla dónde se dirigen inicialmente las visitas de los usuarios. La mayoría de los clientes no utilizan tipos de RDC personalizados.
