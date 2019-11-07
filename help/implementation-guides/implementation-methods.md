---
description: Métodos de implementación estándar y no estándar del servicio de identidad de Experience Cloud.
keywords: Servicio de ID
seo-description: Métodos de implementación estándar y no estándar del servicio de identidad de Experience Cloud.
seo-title: Métodos de implementación
title: Métodos de implementación
uuid: d41250e2-09f4-4a8b-8ade-54d43e9281c9
translation-type: tm+mt
source-git-commit: e75a448a2fa1c384c88f00648a6f868a886c6569

---


# Métodos de implementación

Puede elegir un método de implementación estándar [!DNL Experience Cloud ID Service] usando [!DNL Experience Platform Launch], [!DNL Dynamic Tag Manager] (DTM) o un método no estándar.

>[!IMPORTANT]
>
>Asegúrese de leer y comprender los [requisitos del servicio de ID](../reference/requirements.md) antes de comenzar con estos procedimientos.

## Implementación estándar {#section-ea1e5270f2184f85a2e85214a6ac60cb}

Adobe recomienda encarecidamente usar [!DNL Experience Platform Launch](https://docs.adobe.com/content/help/en/launch/using/implement/solutions/idservice-save.html) para implementar el servicio de ID. Este método garantiza la integración con otras [!DNL Experience Cloud] soluciones, optimiza los flujos de trabajo de implementación y garantiza automáticamente la correcta colocación y secuenciación del código.

## Implementaciones no estándar{#section-2c4f2db1f9704315a7cccab6d2e07113}

The procedures and code samples in this guide can help you set up the [!DNL Experience Cloud] ID service in a manual, or non-standard manner. Observe que estas implementaciones a menudo son técnicamente complejas y difíciles. Es posible que deba asignar recursos de ingeniería específicos, o que termine usando parte de la cuota del servicio de asistencia técnica contratado con su consultor de Adobe.

>[!TIP]
>
>Como alternativa, puede implementar el servicio de ID mediante [!DNL Dynamic Tag Manager](https://docs.adobe.com/content/help/en/dtm/using/dtm-home.html). Sin embargo, los nuevos clientes deben usar [!DNL Experience Platform Launch]. Para actualizar a [!DNL Experience Platform Launch] desde [!DNL Dynamic Tag Manager], consulte [Actualización de DTM a Launch](https://docs.adobe.com/content/help/en/launch/using/reference/upgrade/overview.html)).
