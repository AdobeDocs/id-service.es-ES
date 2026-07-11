---
description: Función del servicio de ID de visitante en Adobe CX Enterprise.
keywords: Servicio de ID de visitante
title: Información general
exl-id: d907e299-bde0-4b5f-8c16-867a4eaa8be1
TQID: https://experienceleague.adobe.com/YUy7gs28-5lGzLmfE-MJ4nRtQc7I05Q4nRCBO4gOdMI
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 336
ht-degree: 25%

---

# Acerca del servicio de ID de visitante{#aboutidservice}

Función del servicio de ID de visitante en Adobe CX Enterprise.

<!--
mcvid-functionality.xml
-->

## El servicio de ID de visitante: un elemento básico de los servicios principales {#section-2de0eb1d65664e92a4d8bbb167b84bde}

El servicio de ID de visitante habilita el marco de identificación común para los servicios principales de CX Enterprise, sus soluciones, los atributos de cliente y las audiencias. Funciona asignando ID únicos y persistentes a los visitantes del sitio. Cuando su organización implementa el servicio de ID de visitante, este ID le permite identificar el mismo visitante del sitio y sus datos en diferentes soluciones de CX Enterprise.

![](assets/ecid-new.png)

Además, el servicio de ID de visitante puede reemplazar los distintos ID específicos de la solución (por ejemplo, Analytics AID). Gracias a la funcionalidad [ID de cliente y estados de autenticación](../reference/authenticated-state.md), el servicio de ID de visitante le permite transferir sus propios ID de cliente a CX Enterprise. Sin embargo, tenga en cuenta que el servicio de ID de visitante solo funciona con las soluciones a las que ya está suscrito. No proporciona acceso a otros productos si no se ha registrado en ellos.

De ahora en adelante, el servicio de ID de visitante será un componente integral de muchas funciones, mejoras y servicios empresariales actuales y futuros de CX. Actualmente, el servicio de identificación del visitante admite [Analytics](http://www.adobe.com/es/marketing-cloud/web-analytics.html), [Audience Manager](http://www.adobe.com/es/marketing-cloud/data-management-platform.html) y [Target](http://www.adobe.com/es/marketing-cloud/testing-targeting.html). Además, es imprescindible para poder participar en Device Co-Op de Adobe. Si no ha implementado el Servicio de ID de visitante, ahora es el momento de empezar a pensar en una estrategia de migración.

## Resumen de características {#section-96555473455c4bf8924c2d56ff4f3255}

En resumen, el servicio de ID de visitante:

* Crea una clave común o ID que se puede utilizar para vincular perfiles e identidades.
* Identifica de forma exclusiva un dispositivo en varias soluciones.
* Establece una cookie de origen en el dominio del cliente para garantizar el seguimiento en el mismo dominio. Consulte [Cookies y el servicio de ID de visitante](../introduction/cookies.md).
* Recibe alias y asignaciones de ID de clientes y socios de CX Enterprise.
* Gestiona la sincronización de ID en CX Enterprise.
* Admite la sincronización de ID con terceros distintos en el ecosistema tecnológico de publicidad.

