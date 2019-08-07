---
description: La función del servicio de identidad de Experience Platform en Adobe Experience Cloud.
seo-description: El servicio de identidad de Experience Platform permite el marco de identificación común para los servicios principales, las soluciones y los atributos del cliente y las audiencias de Experience Cloud.
seo-title: Información general del servicio de ID
title: Información general
uuid: null
translation-type: tm+mt
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# Información general

El servicio de identidad de Experience Platform permite el marco de identificación común de los servicios principales, las soluciones y los atributos del cliente y las audiencias de Experience Cloud en el servicio de identidad de la plataforma. (Puede ver referencias a nombres antiguos o siglas, como Experience Cloud ID Service, ECID, Marketing Cloud ID Service, MID y Visitor ID Service). El servicio de identidad funciona asignando un ID exclusivo y persistente a un visitante del sitio. Cuando la organización implementa el servicio de ID, este ID le permite identificar al mismo visitante del sitio y sus datos en diferentes soluciones de Experience Cloud.

![](assets/ecid.png)

Igualmente, el servicio de ID puede sustituir a los distintos ID específicos de las diferentes soluciones (p. ej., Analytics AID). Y, a través de la funcionalidad [ID de cliente y estados de autenticación](/help/reference/authenticated-state.md), el servicio de ID le permite transferir sus propios ID de cliente a Experience Cloud. No obstante, tenga en cuenta que el servicio de ID solo funciona con las soluciones a las que esté ya suscrito. No proporciona acceso a otros productos si no los tiene registrados.

De ahora en adelante, el servicio de ID será un componente integral de muchas funciones, mejoras y servicios tanto actuales como futuros de Experience Cloud. En la actualidad, el servicio de ID es compatible con [Analytics](http://www.adobe.com/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/marketing-cloud/data-management-platform.html) y [Target](http://www.adobe.com/marketing-cloud/testing-targeting.html). Además, es imprescindible para poder participar en Device Co-Op de Adobe Experience Cloud. Si no ha implementado el servicio de ID, ahora es el momento de empezar a pensar en una estrategia de migración. For more information about the importance and role of the ID service, see [Why the Experience Cloud Identity Service Should be on Your Radar](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/).

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

* [Cookies y servicio de identidad de Experience Cloud](cookies.md): El servicio de ID utiliza su ID de organización, la cookie AMCV de Experience Cloud y una cookie demdex para crear y almacenar identificadores únicos y persistentes para los visitantes del sitio. Estas cookies permiten que el servicio de ID realice un seguimiento de los visitantes entre los distintos dominios del usuario y permiten compartir datos entre las distintas soluciones de Experience Cloud.
* [Cómo solicita y establece los ID el servicio de identidad de Experience Cloud](id-request.md): Información general sobre el proceso de respuesta y solicitud de ID. Estos ejemplos abarcan la asignación de ID en sitios concretos, entre sitios distintos, y para sitios administrados por clientes de Experience Cloud distintos con sus ID de organización propios.
* [Conceptos básicos de sincronización de ID y tasas de coincidencia](match-rates.md): Información general sobre procesos de sincronización de ID y tasas de coincidencia en el servicio de identidad de Experience Cloud, incluido Adobe Media Optimizer y el servicio de ID.