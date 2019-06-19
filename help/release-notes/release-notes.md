---
description: Versiones de funciones, actualizaciones o cambios en el servicio de identidad de Experience Platform.
keywords: Servicio de ID
seo-description: Versiones de funciones, actualizaciones o cambios en el servicio de identidad de Experience Platform.
seo-title: Notas de la versión 2019
title: Notas de la versión 2019
uuid: a 5 a 59410-7 f 85-48 f 9-a 30 a-fef 1 c 2 e 2 b 558
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Notas de la versión 2019 {#release-notes}

Versiones de funciones, actualizaciones o cambios en el servicio de identidad de Experience Platform.

## Notas de la versión 2019 {#topic-1b9a1c3ec5044e1c987785950f697e25}

Versiones de características, actualizaciones o cambios en el servicio de ID de [!DNL Experience Cloud].

## Versión 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Servicio Opt-in**. Opt-in es una extensión de [Experience Cloud ID (ECID)](https://marketing.adobe.com/resources/help/en_US/mcvid/) que permite controlar si las bibliotecas de Experience Cloud pueden crear cookies en las páginas web de los visitantes, y cuáles pueden hacerlo. Mediante el uso de [Launch](https://docs.adobelaunch.com/) puede simplificar la recopilación de consentimientos de inclusión de los visitantes para la solución de Experience Cloud. Habilite Analytics, Target, Audience Manager y otras soluciones de Experience Cloud (o todas ellas) para incluirse en su sistema de administración del consentimiento.

## Versión 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Elemento | Descripción |
|---|---|
| El indicador `disableIdSyncs` no funciona cuando se pasa una cadena | Corregido. Los valores establecidos en `disableidSyncs` el parámetro para `getInstance` la función se están aceptando. |
| Los iFrames de terceros no reciben ECID | Se ha corregido los ECID en la versión móvil de Safari, así como ECID que no funcionaban para distintos iFrames. |

