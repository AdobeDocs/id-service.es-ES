---
description: La función que desempeña el servicio de identidad de Experience Cloud en Adobe Experience Cloud.
title: Información general del servicio de identidad de Experience Cloud
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
source-git-commit: f7c25f5ebd0690c56c081422949eb34f1f277ae1
workflow-type: ht
source-wordcount: '489'
ht-degree: 100%

---

# Información general del servicio de identidad de Experience Cloud

El servicio de identidad de Experience Cloud habilita el marco de identificación común para los servicios de aplicación de Experience Cloud. Puede utilizar el servicio de identidad del Experience Cloud para establecer la variable [ID de Experience Cloud (ECID)](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html?lang=es).

El ECID es un área de nombres de identidad compartida que se utiliza en las aplicaciones de Adobe Experience Platform y Experience Cloud para realizar un seguimiento del comportamiento de los visitantes y garantizar que cada dispositivo tenga un identificador único que pueda persistir en varias sesiones.

>[!TIP]
>
>El servicio de identidad de Experience Cloud, el servicio de identidad de Experience Platform y ECID son tres **diferentes** entidades.

El servicio de identidad de Experience Cloud puede reemplazar distintos ID específicos de la aplicación y usar la funcionalidad [ID de cliente y estados de autenticación](/help/reference/authenticated-state.md) para permitirle pasar sus propios ID de cliente al Experience Cloud.

>[!NOTE]
>
>El servicio de identidad de Experience Cloud solo funciona con los Servicios de aplicación de Experience Cloud a los que está suscrito y no proporcionará acceso a otros servicios de aplicación si no está suscrito a ellos.

El servicio de identidad de Experience Cloud admite las siguientes aplicaciones:

* [Adobe Analytics](https://business.adobe.com/es/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/es/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/es/products/target/adobe-target.html)

De ahora en adelante, el servicio de ID será un componente integral de muchas funciones, mejoras y servicios tanto actuales como futuros de Experience Cloud. En la actualidad, el servicio de ID es compatible con [Analytics](http://www.adobe.com/es/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/es/marketing-cloud/data-management-platform.html) y [Target](http://www.adobe.com/es/marketing-cloud/testing-targeting.html). Si no ha implementado el servicio de ID, ahora es el momento de empezar a pensar en una estrategia de migración.

## Resumen de características

En resumen, el servicio de identidad de Experience Cloud ayuda a:

* Identifica de forma exclusiva a un visitante en un dispositivo en varias aplicaciones.
* Establece una cookie de origen en el dominio del cliente para garantizar el seguimiento en el mismo dominio. Consulte el documento sobre [cookies y el servicio de identidad de Experience Cloud](./cookies.md) para obtener más información.
* Recibe alias y asignaciones de ID de clientes y socios de Experience Cloud.
* Gestiona la sincronización de ID en Experience Cloud.
* Admite la sincronización de ID con terceros distintos en el ecosistema tecnológico de publicidad.

## Requisitos del servicio de identidad de Experience Cloud

Su solución y otras bibliotecas de código de Adobe deben cumplir con [ciertos requisitos](/help/reference/requirements.md) antes de poder usar el servicio de identidad.

* [Cookies y el servicio de Experience Cloud ID](cookies.md): el servicio de identidad utiliza su ID de organización, la cookie AMCV de Experience Cloud y una cookie demdex a fin de crear y almacenar ID únicos y persistentes para los visitantes de su sitio. Estas cookies permiten que el servicio de ID realice un seguimiento de los visitantes entre los distintos dominios del usuario y permiten compartir datos entre las distintas soluciones de Experience Cloud.
* [Solicitud y configuración de ID con el servicio de identidad de Experience Cloud](id-request.md): Información general sobre el proceso de respuesta y solicitud de ID. Estos ejemplos abarcan la asignación de ID en sitios concretos, entre sitios distintos, y para sitios administrados por clientes de Experience Cloud distintos con sus ID de organización propios.
* [Conceptos básicos de la sincronización de ID y tasas de coincidencia](match-rates.md): resumen de los procesos de sincronización de ID y las tasas de coincidencia en el servicio de identidad de Experience Cloud, incluidos Adobe Media Optimizer y el servicio de identidad.
