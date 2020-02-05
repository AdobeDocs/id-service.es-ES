---
description: Función del servicio Experience Cloud Identity en Adobe Experience Cloud.
seo-description: El servicio de identidad de Experience Cloud (anteriormente servicio de ID de visitante o servicio de Marketing Cloud ID) habilita el marco de identificación común para los servicios de Experience Cloud, como los atributos y las audiencias del cliente.
seo-title: Descripción general del servicio Experience Cloud ID
title: Descripción general del servicio Experience Cloud ID
translation-type: tm+mt
source-git-commit: 9e020c3292a7c9f14ec77615a54ec61a37762eec

---


# Descripción general del servicio Experience Cloud ID

The [!UICONTROL Experience Cloud Identity Service] enables the common identification framework for Experience Cloud Core Services (such as customer attributes and audiences) solutions in the Experience Platform Identity Service.

>[!NOTE]
>
> Puede ver referencias a nombres o siglas anteriores, como ECID, Servicio de Marketing Cloud ID (MID) y Servicio de ID de visitante. Se refieren al servicio [!UICONTROL de identidad de]Experience Cloud. También puede ver el servicio [!UICONTROL de identidad de la plataforma de]experiencia. Para aclarar:

* [!UICONTROL Servicio]de identidad de la plataforma de experiencia: El servicio que vincula identidades. Es el servicio de vinculación de dispositivos para la administración de experiencias basadas en personas.
* [!UICONTROL Servicio] Experience Cloud ID (ECID): ID única y persistente asignada a un visitante del sitio. Es una entidad específica que puede ser utilizada por el servicio de identidad de plataforma.

Cuando la organización implementa el servicio de ID, este ID le permite identificar al mismo visitante del sitio y sus datos en diferentes soluciones de Experience Cloud.

![](assets/ecid.png)

Igualmente, el servicio de ID puede sustituir a los distintos ID específicos de las diferentes soluciones (p. ej., Analytics AID). Y, a través de la funcionalidad [ID de cliente y estados de autenticación](/help/reference/authenticated-state.md), el servicio de ID le permite transferir sus propios ID de cliente a Experience Cloud. No obstante, tenga en cuenta que el servicio de ID solo funciona con las soluciones a las que esté ya suscrito. No proporciona acceso a otros productos si no los tiene registrados.

De ahora en adelante, el servicio de ID será un componente integral de muchas funciones, mejoras y servicios tanto actuales como futuros de Experience Cloud. En la actualidad, el servicio de ID es compatible con [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html) y [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html). Además, es imprescindible para poder participar en Device Co-Op de Adobe Experience Cloud. Si no ha implementado el servicio de ID, ahora es el momento de empezar a pensar en una estrategia de migración. Para obtener más información acerca de la importancia y la función que desempeña el servicio de ID, consulte [Por qué debería plantearse el servicio de Experience Cloud ID](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/).

## Resumen de características

En resumen, el servicio de ID:

* Crea una clave común o ID que se puede utilizar para vincular perfiles e identidades.
* Identifica de forma exclusiva un dispositivo en varias soluciones.
* Establece una cookie de origen en el dominio de un cliente para garantizar que se realiza el seguimiento en un mismo dominio. Consulte Experience Cloud.
* Recibe alias y asignaciones de ID de clientes y socios de Experience Cloud.
* Gestiona la sincronización de ID en Experience Cloud.
* Admite la sincronización de ID con terceros distintos en el ecosistema tecnológico de publicidad.

## Requisitos del servicio de ID

Su solución y demás bibliotecas de código de Adobe deben cumplir con [determinados requisitos](/help/reference/requirements.md) para poder hacer uso del servicio de ID.

* [Cookies y el servicio de identidad de Experience Cloud](cookies.md): El servicio de identidad utiliza su ID de organización, la cookie AMCV de Experience Cloud y una cookie demdex a fin de crear y almacenar identificadores únicos y persistentes para los visitantes de su sitio. Estas cookies permiten que el servicio de ID realice un seguimiento de los visitantes entre los distintos dominios del usuario y permiten compartir datos entre las distintas soluciones de Experience Cloud.
* [Solicitud y configuración de ID con el servicio de identidad de Experience Cloud](id-request.md): Información general sobre el proceso de respuesta y solicitud de ID. Estos ejemplos abarcan la asignación de ID en sitios concretos, entre sitios distintos, y para sitios administrados por clientes de Experience Cloud distintos con sus ID de organización propios.
* [Conceptos básicos de la sincronización de ID y tasas de coincidencia](match-rates.md): Resumen de los procesos de sincronización de ID y las tasas de coincidencia en el servicio de identidad de Experience Cloud, incluidos Adobe Media Optimizer y el servicio de identidad.