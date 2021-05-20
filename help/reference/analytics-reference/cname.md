---
description: Si tiene un sitio de entrada principal en el que se puede identificar a los clientes antes de que visiten otros dominios, un registro CNAME puede habilitar el seguimiento entre dominios en los exploradores que no acepten cookies de terceros (como Safari).
keywords: orden de operaciones; servicio de ID
seo-description: Si tiene un sitio de entrada principal en el que se puede identificar a los clientes antes de que visiten otros dominios, un registro CNAME puede habilitar el seguimiento entre dominios en los exploradores que no acepten cookies de terceros (como Safari).
seo-title: Información general sobre la implementación de CNAME
title: Información general sobre la implementación de CNAME
uuid: ba42c822-b677-4139-b1ed-4d98d3320fd0
translation-type: ht
source-git-commit: ebeca9e285af71872c05d58ba252ca65bde24f3d
workflow-type: ht
source-wordcount: '259'
ht-degree: 100%

---


# Información general sobre la implementación de CNAME {#cname-implementation-overview}

Las implementaciones de CNAME le permiten personalizar el dominio de colección que utiliza Adobe para que coincida con su propio dominio. Esto permite a Adobe establecer cookies de origen del lado del servidor en lugar de hacerlo en el lado del cliente mediante JavaScript. En el pasado, estas cookies de origen del lado del servidor no estaban sujetas a los límites impuestos por la directiva de prevención inteligente del seguimiento (ITP) de Apple. Sin embargo, en noviembre de 2020, [!DNL Apple] actualizó sus directivas para que estas limitaciones también se aplicaran a las cookies configuradas mediante CNAME. Actualmente, ambas cookies configuradas del lado del servidor mediante CNAME y las cookies configuradas del lado del cliente mediante JavaScript están limitadas a una caducidad de siete días o de 24 horas en ITP. Para obtener más información sobre la directiva ITP, consulte este [!DNL Apple] documento [sobre la prevención de seguimiento](https://webkit.org/tracking-prevention/#intelligent-tracking-prevention-itp).

Aunque la implementación de CNAME no proporciona ningún beneficio en cuanto a la duración de las cookies, puede haber otros beneficios, como bloqueadores de anuncios y exploradores menos comunes, que impiden que se envíen datos a dominios que pueden conocerse como rastreadores. En estos casos, el uso de un CNAME puede impedir que la recopilación de datos se interrumpa para los usuarios que utilizan estas herramientas.