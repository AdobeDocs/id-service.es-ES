---
description: Preguntas más frecuentes sobre las características, la funcionalidad y los problemas relativos a otras soluciones de Experience Cloud con el servicio de ID.
keywords: Servicio de ID
title: Preguntas frecuentes para otras soluciones de Experience Cloud
exl-id: d1164951-01c9-4375-981a-f87d8a280e4b
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 100%

---

# Preguntas frecuentes para otras soluciones de Experience Cloud {#faqs-for-other-experience-cloud-solutions}

Preguntas más frecuentes sobre las características, la funcionalidad y los problemas relativos a otras soluciones de Experience Cloud con el servicio de ID.

## Dynamic Tag Management (DTM) {#section-7ac4b9c1f1fd45a5a03eac3fb5968af7}

**¿Puedo utilizar la Dynamic Tag Management para implementar el servicio de ID de visitante?**

Sí, esta es la opción de implementación preferida y recomendada.

Consulte [Implementación estándar con DTM](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445).

## Analytics y Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**¿El historial de visitas de un usuario se exporta de [!DNL Adobe Analytics] a [!DNL Audience Manager] después de implementar el servicio de identidad de Experience Cloud?**

Aquí existen dos opciones:

* Si un usuario realiza cualquier actividad de visitante una vez implementado el servicio de ID, el visitante y su historial se incluyen en la exportación de datos a [!DNL Audience Manager].
* Si un usuario no realiza ninguna actividad de visita una vez implementado el servicio de ID, el visitante y su historial no se incluirán en la exportación de datos a Audience Manager. Como no existe nueva actividad, no hay modo de asociar el ID de Analytics con el Experience Cloud ID.
