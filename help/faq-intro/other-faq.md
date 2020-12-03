---
description: Preguntas más frecuentes sobre las características, la funcionalidad y los problemas relativos a otras soluciones de Experience Cloud con el servicio de ID.
keywords: ID Service
seo-description: Preguntas más frecuentes sobre las características, la funcionalidad y los problemas relativos a otras soluciones de Experience Cloud con el servicio de ID.
seo-title: Preguntas frecuentes para otras soluciones de Experience Cloud
title: Preguntas frecuentes para otras soluciones de Experience Cloud
uuid: 7d848663-6cbb-4d80-ab06-7b6d2dc20e2b
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 72%

---


# Preguntas frecuentes para otras soluciones de Experience Cloud{#faqs-for-other-experience-cloud-solutions}

Preguntas más frecuentes sobre las características, la funcionalidad y los problemas relativos a otras soluciones de Experience Cloud con el servicio de ID.

## Dynamic Tag Management (DTM) {#section-7ac4b9c1f1fd45a5a03eac3fb5968af7}

**¿Puedo utilizar la administración dinámica de etiquetas para implementar el servicio de ID de visitante?**

Sí, esta es la opción de implementación preferida y recomendada.

See [Standard Implementation with DTM](../implementation-guides/standard.md#concept-89cd0199a9634fc48644f2d61e3d2445).

## Analytics y Audience Manager {#section-b3dd206d497041acb04554c6fb1c912a}

**¿El historial de visitas de un usuario se exporta de [!DNL Adobe Analytics] a [!DNL Audience Manager] después de implementar el servicio de identidad de Experience Cloud?**

Aquí existen dos opciones:

* Si un usuario realiza cualquier actividad de visitante una vez implementado el servicio de ID, el visitante y su historial se incluyen en la exportación de datos a [!DNL Audience Manager].
* Si un usuario no tiene ninguna actividad de visita después de implementar el servicio de ID, el visitante y su historial no se incluirán en la exportación de datos a Audience Manager. Como no existe nueva actividad, no hay modo de asociar el ID de Analytics con el Experience Cloud ID.

