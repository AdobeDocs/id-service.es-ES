---
description: La función que desempeña el servicio de identidad de Experience Cloud en Adobe Experience Cloud.
title: Introducción al servicio de Experience Cloud ID
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
source-git-commit: 2c87022baeb09a8767d0d9627bf2b607c51b2503
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Introducción al servicio de Experience Cloud ID

El [!UICONTROL servicio de identidad de Experience Cloud] activa las soluciones del marco común de identificación para los servicios principales de Experience Cloud (como los atributos de cliente y audiencias) en el servicio de identidad de Experience Platform.

>[!NOTE]
>
> Puede ver referencias al servicio de ID como acrónimos o nombres anteriores, como ECID, Servicio de Experience Cloud ID (MID) y Servicio de ID de visitante. Se refieren al [!UICONTROL servicio de identidad de Experience Cloud]. También puede ver el [!UICONTROL servicio de identidad de Experience Platform]. Para aclarar:

* [!UICONTROL Servicio de identidad de Experience Platform]: El servicio que vincula identidades. Es el servicio de vinculación de dispositivos para la administración de experiencias individualizadas.
* [!UICONTROL Servicio de Experience Cloud ID] (ECID): ID único y persistente asignada a un visitante del sitio. Es una entidad específica que puede utilizar Identity Service de Platform

Cuando su organización implementa el servicio de ID, este ID le permite identificar el mismo visitante del sitio y sus datos en diferentes soluciones de Experience Cloud.

![](assets/ecid-new.png)

Además, el servicio de ID puede reemplazar los distintos ID específicos de la solución (por ejemplo, Analytics AID). Gracias a la funcionalidad [ID de cliente y a los estados de autenticación](/help/reference/authenticated-state.md), el servicio de ID le permite transferir sus propios ID de cliente a Experience Cloud. Sin embargo, tenga en cuenta que el servicio de ID solo funciona con las soluciones a las que ya está suscrito. No proporciona acceso a otros productos si no se ha registrado en ellos.

De ahora en adelante, el servicio de ID será un componente integral de muchas funciones, mejoras y servicios tanto actuales como futuros de Experience Cloud. En la actualidad, el servicio de ID es compatible con [Analytics](http://www.adobe.com/es/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/es/marketing-cloud/data-management-platform.html) y [Target](http://www.adobe.com/es/marketing-cloud/testing-targeting.html). Además, es imprescindible para poder participar en Device Co-Op de Adobe Experience Cloud. Si no ha implementado el servicio de ID, ahora es el momento de empezar a pensar en una estrategia de migración.

## Resumen de características

En resumen, el servicio de ID hace lo siguiente:

* Crea una clave común o ID que se puede utilizar para vincular perfiles e identidades.
* Identifica de forma exclusiva un dispositivo en varias soluciones.
* Establece una cookie de origen en el dominio del cliente para garantizar el seguimiento en el mismo dominio. Consulte el documento sobre [cookies y el servicio de identidad de Experience Cloud](./cookies.md) para obtener más información.
* Recibe alias y asignaciones de ID de clientes y socios de Experience Cloud.
* Gestiona la sincronización de ID en Experience Cloud.
* Admite la sincronización de ID con terceros distintos en el ecosistema tecnológico de publicidad.

## Requisitos del servicio de ID

Su solución y demás bibliotecas de código de Adobe deben cumplir con [determinados requisitos](/help/reference/requirements.md) para poder hacer uso del servicio de ID.

* [Cookies y el servicio de Experience Cloud ID](cookies.md): El servicio de identidad utiliza su ID de organización, la cookie AMCV de Experience Cloud y una cookie demdex a fin de crear y almacenar ID únicos y persistentes para los visitantes de su sitio. Estas cookies permiten que el servicio de ID realice un seguimiento de los visitantes entre los distintos dominios del usuario y permiten compartir datos entre las distintas soluciones de Experience Cloud.
* [Solicitud y configuración de ID con el servicio de identidad de Experience Cloud](id-request.md): Información general sobre el proceso de respuesta y solicitud de ID. Estos ejemplos abarcan la asignación de ID en sitios concretos, entre sitios distintos, y para sitios administrados por clientes de Experience Cloud distintos con sus ID de organización propios.
* [Conceptos básicos de la sincronización de ID y tasas de coincidencia](match-rates.md): Resumen de los procesos de sincronización de ID y las tasas de coincidencia en el servicio de identidad de Experience Cloud, incluidos Adobe Media Optimizer y el servicio de identidad.
