---
description: El servicio de ID de visitante de Adobe habilita el marco de identificación común para la aplicación y los servicios empresariales de CX. Funciona asignando un ID único y persistente conocido como ECID a un visitante del sitio.
keywords: Servicio de ID de visitante; ECID
title: Servicio de ID de visitante de Adobe
exl-id: fe1368db-06ca-4c79-b655-b7064e316d74
TQID: https://experienceleague.adobe.com/xzEgzuN2NnyOnhCPocQikOXHFRU6zmLWLGdrJL4C3GM
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 410
ht-degree: 28%

---

# Servicio de ID de visitante de Adobe {#experience-cloud-id-service}

>[!BEGINSHADEBOX]

El servicio de identificación de visitante es **no** el [servicio de identidad de Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=es). El servicio de ID de visitante es la biblioteca de JavaScript `VisitorAPI.js` que se describe en esta guía y que establece el ECID para Adobe Analytics, Audience Manager y Target. Si está buscando el servicio de Adobe Experience Platform que resuelve identidades entre dispositivos y sistemas en un perfil unificado de cliente, consulte la [descripción general del servicio de identidad de Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=es).

>[!ENDSHADEBOX]

El servicio de ID de visitante de Adobe habilita el marco de identificación común para la aplicación y los servicios empresariales de CX. Funciona asignando un ID único y persistente conocido como ECID a un visitante del sitio.

## Explicación de las principales entidades de identidad

Para comprender mejor cómo Adobe ayuda a identificar visitantes de forma exclusiva y a resolver la información de identidad, lea el desglose siguiente:

* **Servicio de ID de visitante**: El servicio de ID de visitante **es responsable de configurar el ECID**. Para obtener más información, lea la [descripción general del servicio de ID de visitante](./introduction/overview.md).
* **ECID**: ECID es un área de nombres de identidad compartida que se usa en las aplicaciones empresariales de Adobe Experience Platform y Adobe CX para identificar personas y dispositivos. Para obtener más información sobre el ECID, lea la [Información general de ECID](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/ecid).
* **Servicio de identidad de Experience Platform**: el servicio de identidad de Experience Platform le ofrece una vista completa de sus clientes y de su comportamiento al unir identidades entre dispositivos y sistemas. Para obtener más información, lea [Información general del servicio de identidad de Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=es).

## Introducción

* [Descripción general del servicio de ID de visitante](introduction/overview.md): Descubra lo que hace el servicio de ID de visitante y cómo encaja en CX Enterprise.
* [Requisitos del servicio de ID de visitante](reference/requirements.md): confirme que sus soluciones y bibliotecas de código cumplen los requisitos previos para implementar el servicio de ID de visitante.
* [Métodos de implementación](implementation-guides/implementation-methods.md): Compare la implementación estándar usando [etiquetas](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=es) con métodos de integración directa no estándar.

## Explora la documentación

**Implementación**

* [Guías de implementación](implementation-guides/implementation-guides.md)
* [Integración directa con el servicio de ID de visitante](implementation-guides/direct-integration.md)
* [Información general sobre el servicio Opt-in](implementation-guides/opt-in-service/optin-overview.md)
* [Comprobación y verificación del servicio de ID de visitante](implementation-guides/test-verify.md)

**Referencia de API**

* [Resumen de API del servicio de ID de visitante](library/library.md)
* [getVisitorValues](library/get-set/getvisitorvalues.md)
* [idSyncContainerID](library/function-vars/idsyncontainerid.md)

**Preguntas frecuentes**

* [Preguntas frecuentes sobre el servicio de ID de visitante](faq-intro/faq.md)
* [Preguntas frecuentes para otras soluciones de CX Enterprise](faq-intro/other-faq.md)

## Recursos adicionales

* [Versiones de la biblioteca JavaScript de ECID](https://github.com/Adobe-Marketing-Cloud/id-service/releases) en GitHub
* [Notas de la versión del servicio de ID de visitante](release-notes/notes-2022.md)
* [Centro de privacidad de Adobe](http://www.adobe.com/es/privacy.html)
* [Documentación de Adobe CX Enterprise](https://experienceleague.adobe.com/docs/home.html?lang=es)

