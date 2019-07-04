---
description: La función que desempeña el servicio Experience Cloud ID en Adobe Experience Cloud.
seo-description: El servicio Experience Cloud ID habilita el marco de identificación común para los servicios principales de Experience Cloud, sus soluciones, los atributos de cliente y las audiencias en el servicio principal Personas.
seo-title: Información general del servicio de ID
title: Información general
uuid: null
translation-type: ht
source-git-commit: 1c6dc1871ee2e7b8d1f510576836519f7383b809

---


# Información general

El servicio Experience Cloud ID habilita el marco de identificación común para los servicios principales de Experience Cloud, sus soluciones, los atributos de cliente y las audiencias en el servicio principal Personas. Funciona asignando ID únicos y persistentes a los visitantes del sitio. Cuando la organización implementa el servicio de ID, este ID le permite identificar al mismo visitante del sitio y sus datos en diferentes soluciones de Experience Cloud.

![](assets/ecid.png)

Igualmente, el servicio de ID puede sustituir a los distintos ID específicos de las diferentes soluciones (p. ej., Analytics AID). Y, a través de la funcionalidad [ID de cliente y estados de autenticación](/help/mcvid-reference/mcvid-authenticated-state.md), el servicio de ID le permite transferir sus propios ID de cliente a Experience Cloud. No obstante, tenga en cuenta que el servicio de ID solo funciona con las soluciones a las que esté ya suscrito. No proporciona acceso a otros productos si no los tiene registrados.

De ahora en adelante, el servicio de ID será un componente integral de muchas funciones, mejoras y servicios tanto actuales como futuros de Experience Cloud. Actualmente, el servicio de ID admite [Analytics](http://www.adobe.com/es/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/es/marketing-cloud/data-management-platform.html) y [Target](http://www.adobe.com/es/marketing-cloud/testing-targeting.html). Además, es imprescindible para poder participar en Device Co-Op de Adobe Experience Cloud. Si no ha implementado el servicio de ID, ahora es el momento de empezar a pensar en una estrategia de migración. Para obtener más información acerca de la importancia y la función que desempeña el servicio de ID, consulte [Why the Experience Cloud ID Service Should be on Your Radar (Por qué debería plantearse el servicio Experience Cloud ID)](http://blogs.adobe.com/digitalmarketing/analytics/why-new-adobe-marketing-cloud-id-service-should-be-on-your-radar/).

## Resumen de características

En resumen, el servicio de ID:

* Crea una clave común o ID que se puede utilizar para vincular perfiles e identidades.
* Identifica de forma exclusiva un dispositivo en varias soluciones.
* Establece una cookie de origen en el dominio de un cliente para garantizar que se realiza el seguimiento en un mismo dominio. Consulte Experience Cloud.
* Recibe alias y asignaciones de ID de clientes y socios de Experience Cloud.
* Gestiona la sincronización de ID en Experience Cloud.
* Admite la sincronización de ID con terceros distintos en el ecosistema tecnológico de publicidad.

## Requisitos del servicio de ID

Su solución y demás bibliotecas de código de Adobe deben cumplir con [determinados requisitos](/help/mcvid-reference/mcvid-requirements.md) para poder hacer uso del servicio de ID.

* [Cookies y el servicio de Experience Cloud ID](mcvid-cookies.md): El servicio de ID utiliza su ID de organización, la cookie AMCV de Experience Cloud y una cookie demdex a fin de crear y almacenar identificadores únicos y persistentes para los visitantes de su sitio. Estas cookies permiten que el servicio de ID realice un seguimiento de los visitantes entre los distintos dominios del usuario y permiten compartir datos entre las distintas soluciones de Experience Cloud.
* [Solicitud y configuración de ID con el servicio de Experience Cloud ID](mcvid-id-request.md): Información general sobre el proceso de respuesta y solicitud de ID. Estos ejemplos abarcan la asignación de ID en sitios concretos, entre sitios distintos, y para sitios administrados por clientes de Experience Cloud distintos con sus ID de organización propios.
* [Conceptos básicos de la sincronización de ID y tasas de coincidencia](mcvid-match-rates.md): Un resumen de los procesos de sincronización de ID y las tasas de coincidencia en el servicio Experience Cloud ID, incluidos Adobe Media Optimizer y el servicio de ID.