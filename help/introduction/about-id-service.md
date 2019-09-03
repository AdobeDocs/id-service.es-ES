---
description: La función que desempeña el servicio de Experience Platform ID en Adobe Experience Cloud.
keywords: Servicio de ID
seo-description: La función que desempeña el servicio de Experience Platform ID en Adobe Experience Cloud.
seo-title: Acerca del servicio de ID
title: Información general
uuid: c52d6155-00a0-4fc5-9d8e-5ce00b8d01e6
translation-type: ht
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# Acerca del servicio de ID{#aboutidservice}

La función que desempeña el servicio de identidad de Experience Cloud en Adobe Experience Cloud.

<!--
mcvid-functionality.xml
-->

## El servicio de identidad de Experience Cloud: un elemento básico de los servicios principales {#section-2de0eb1d65664e92a4d8bbb167b84bde}

El servicio de identidad de Experience Cloud admite el marco de identificación común para los servicios principales de Experience Cloud, las soluciones y los atributos y audiencias de los clientes. Funciona asignando ID únicos y persistentes a los visitantes del sitio. Cuando la organización implementa el servicio de ID, este ID le permite identificar al mismo visitante del sitio y sus datos en diferentes soluciones de Experience Cloud.

![](assets/ecid.png)

Igualmente, el servicio de ID puede sustituir a los distintos ID específicos de las diferentes soluciones (p. ej., Analytics AID). Y, a través de la funcionalidad [ID de cliente y estados de autenticación](../reference/authenticated-state.md), el servicio de ID le permite transferir sus propios ID de cliente a [!DNL Experience Cloud]. No obstante, tenga en cuenta que el servicio de ID solo funciona con las soluciones a las que esté ya suscrito. No proporciona acceso a otros productos si no los tiene registrados.

De ahora en adelante, el servicio de ID será un componente integral de muchas funciones, mejoras, y servicios actuales y [!DNL Experience Cloud] futuros de. Actualmente, el servicio de ID admite [Analytics](http://www.adobe.com/es/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/es/marketing-cloud/data-management-platform.html) y [Target](http://www.adobe.com/es/marketing-cloud/testing-targeting.html). Además, es imprescindible para poder participar en [!DNL Adobe Experience Cloud] Device Co-Op de. Si no ha implementado el servicio de ID, ahora es el momento de empezar a pensar en una estrategia de migración. Para obtener más información acerca de la importancia y la función que desempeña el servicio de ID, consulte [Por qué debería plantearse el servicio de Experience Cloud ID](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/).

## Resumen de características {#section-96555473455c4bf8924c2d56ff4f3255}

En resumen, el servicio de ID:

* Crea una clave común o ID que se puede utilizar para vincular perfiles e identidades.
* Identifica de forma exclusiva un dispositivo en varias soluciones.
* Establece una cookie de origen en el dominio de un cliente para garantizar que se realiza el seguimiento en un mismo dominio. Consulte [Experience Cloud](../introduction/cookies.md).
* Recibe alias y asignaciones de ID de [!DNL Experience Cloud] clientes y socios.
* Gestiona la sincronización de ID en [!DNL Experience Cloud].
* Admite la sincronización de ID con terceros distintos en el ecosistema tecnológico de publicidad.
