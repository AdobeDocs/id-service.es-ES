---
description: La función del servicio de identidad de Experience Platform en Adobe Experience Cloud.
keywords: Servicio de ID
seo-description: La función del servicio de identidad de Experience Platform en Adobe Experience Cloud.
seo-title: Acerca del servicio de ID
title: 'Información general  '
uuid: c 52 d 6155-00 a 0-4 fc 5-9 d 8 e -5 ce 00 b 8 d 01 e 6
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Acerca del servicio de ID{#aboutidservice}

La función del servicio de identidad de Experience Platform en Adobe Experience Cloud.

<!--
mcvid-functionality.xml
-->

## Servicio de identidad de la plataforma de experiencia: Elemento básico de los servicios principales {#section-2de0eb1d65664e92a4d8bbb167b84bde}

El servicio de identidad de la plataforma de experiencia habilita el marco de identificación común para los servicios principales, las soluciones y los atributos del cliente y las audiencias del cliente en el servicio principal Personas. Funciona asignando ID únicos y persistentes a los visitantes del sitio. Cuando la organización implementa el servicio de ID, este ID le permite identificar al mismo visitante del sitio y sus datos en diferentes soluciones de Experience Cloud.

![](assets/ecid.png)

Igualmente, el servicio de ID puede sustituir a los distintos ID específicos de las diferentes soluciones (p. ej., Analytics AID). Y, a través de la funcionalidad [ID de cliente y estados de autenticación](../reference/authenticated-state.md), el servicio de ID le permite transferir sus propios ID de cliente a [!DNL Experience Cloud]. No obstante, tenga en cuenta que el servicio de ID solo funciona con las soluciones a las que esté ya suscrito. No proporciona acceso a otros productos si no los tiene registrados.

De ahora en adelante, el servicio de ID será un componente integral de muchas funciones, mejoras, y servicios actuales y futuros de [!DNL Experience Cloud]. En la actualidad, el servicio de ID es compatible con [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html) y [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html). Además, es imprescindible para poder participar en Device Co-Op de [!DNL Adobe Experience Cloud]. Si no ha implementado el servicio de ID, ahora es el momento de empezar a pensar en una estrategia de migración. Para obtener más información sobre la importancia y la función del servicio de ID, consulte [Por qué el servicio de identidad de la plataforma de experiencia debería estar en su radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/).

## Resumen de características {#section-96555473455c4bf8924c2d56ff4f3255}

En resumen, el servicio de ID:

* Crea una clave común o ID que se puede utilizar para vincular perfiles e identidades.
* Identifica de forma exclusiva un dispositivo en varias soluciones.
* Establece una cookie de origen en el dominio de un cliente para garantizar que se realiza el seguimiento en un mismo dominio. Consulte [Experience Cloud](../introduction/cookies.md).
* Recibe alias y asignaciones de ID de clientes y socios de [!DNL Experience Cloud].
* Gestiona la sincronización de ID dentro de [!DNL Experience Cloud]la.
* Admite la sincronización de ID con terceros distintos en el ecosistema tecnológico de publicidad.
