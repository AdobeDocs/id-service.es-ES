---
description: Función del servicio de ID de visitante en Adobe CX Enterprise.
title: Introducción al servicio de ID de visitante de Adobe
exl-id: dc7d6220-d42b-4a3e-bf37-1e4e87280ae1
TQID: https://experienceleague.adobe.com/fkT81V3iLEz2irg-3SDoyx733RNhqa2zWV1FgiXoYO4
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 497
ht-degree: 18%

---

# Introducción al servicio de ID de visitante de Adobe

El servicio de ID de visitante de Adobe habilita el marco de identificación común para los servicios de aplicaciones empresariales de CX. Puede usar el servicio de ID de visitante para establecer el [ECID](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html?lang=es).

El ECID es un área de nombres de identidad compartida que se utiliza en las aplicaciones de Adobe Experience Platform y CX Enterprise para realizar un seguimiento del comportamiento de los visitantes y garantizar que cada dispositivo tenga un identificador único que pueda persistir en varias sesiones.

>[!TIP]
>
>El servicio de ID de visitante, el servicio de identidad de Experience Platform y el ECID son tres **entidades diferentes**.

El servicio de ID de visitante puede reemplazar distintos ID específicos de la aplicación y usar la funcionalidad [ID de cliente y estados de autenticación](/help/reference/authenticated-state.md) para permitirle pasar sus propios ID de cliente a CX Enterprise.

>[!NOTE]
>
>El servicio de ID de visitante sólo funciona con los servicios de aplicaciones empresariales de CX a los que está suscrito y no proporcionará acceso a otros servicios de aplicaciones si no está suscrito a ellos.

El servicio de ID de visitante admite las siguientes aplicaciones:

* [Adobe Analytics](https://business.adobe.com/es/products/analytics/web-analytics.html)
* [Audience Manager](https://business.adobe.com/es/products/audience-manager/adobe-audience-manager.html)
* [Adobe Target](https://business.adobe.com/es/products/target/adobe-target.html)

De ahora en adelante, el servicio de ID de visitante será un componente integral de muchas funciones, mejoras y servicios empresariales actuales y futuros de CX. Actualmente, el servicio de identificación del visitante admite [Analytics](http://www.adobe.com/es/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/es/marketing-cloud/data-management-platform.html) y [Target](http://www.adobe.com/es/marketing-cloud/testing-targeting.html). Si no ha implementado el Servicio de ID de visitante, ahora es el momento de empezar a pensar en una estrategia de migración.

## Resumen de características

En resumen, el servicio de ID de visitante ayuda a:

* Identifica de forma exclusiva a un visitante en un dispositivo en varias aplicaciones.
* Establece una cookie de origen en el dominio del cliente para garantizar el seguimiento en el mismo dominio. Consulte el documento sobre [cookies y el servicio de ID de visitante](./cookies.md) para obtener más información.
* Recibe alias y asignaciones de ID de clientes y socios de CX Enterprise.
* Gestiona la sincronización de ID en CX Enterprise.
* Admite la sincronización de ID con terceros distintos en el ecosistema tecnológico de publicidad.

## Requisitos del servicio de ID de visitante

Su solución y otras bibliotecas de código de Adobe deben cumplir con [ciertos requisitos](/help/reference/requirements.md) para poder usar el servicio de identificación del visitante.

* [Cookies y el servicio de ID de visitante](cookies.md): El servicio de ID de visitante utiliza su ID de organización de IMS, la cookie AMCV de CX Enterprise y una cookie demdex a fin de crear y almacenar ID únicos y persistentes para los visitantes de su sitio. Estas cookies permiten que el servicio de ID de visitante realice un seguimiento de los visitantes entre los distintos dominios del usuario y permiten compartir datos entre las distintas soluciones de CX Enterprise.
* [Solicitud y configuración de ID con el servicio de ID de visitante](id-request.md): Información general sobre el proceso de respuesta y solicitud de ID. Estos ejemplos abarcan la asignación de ID en sitios individuales, entre sitios diferentes y para sitios administrados por clientes de CX Enterprise diferentes con sus propios ID de organización de IMS.
* [Conceptos básicos de la sincronización de ID y tasas de coincidencia](match-rates.md): Resumen de los procesos de sincronización de ID y las tasas de coincidencia en el servicio de ID de visitante, incluidos Adobe Media Optimizer y el servicio de ID de visitante.

