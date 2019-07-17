---
description: Versiones de funciones, actualizaciones o cambios en el servicio de identidad de Experience Cloud.
keywords: Servicio de ID
seo-description: Versiones de funciones, actualizaciones o cambios en el servicio de identidad de Experience Cloud.
seo-title: Notas de la versión 2019
title: Notas de la versión 2019
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Notas de la versión 2019 {#release-notes}

Versiones de funciones, actualizaciones o cambios en el servicio de identidad de Experience Cloud.

## Notas de la versión 2019 {#topic-1b9a1c3ec5044e1c987785950f697e25}

Versiones de características, actualizaciones o cambios en el servicio de ID de [!DNL Experience Cloud].

## Versión 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Servicio Opt-in**. La inclusión es una extensión del ID de Experience Cloud (ECID) que permite controlar si las bibliotecas de Experience Cloud pueden crear cookies en páginas web para visitantes (y luego cuáles). Using [Experience Platform Launch](https://docs.adobelaunch.com/), you can simplify gathering visitor opt-in consents for Experience Cloud solution by enabling Analytics, Target, Audience Manager, and other or all select Experience Cloud solutions to opt-in to your consent management system.

## Versión 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Elemento | Descripción |
|---|---|
| El indicador `disableIdSyncs` no funciona cuando se pasa una cadena | Solucionado. Ahora se aceptan los valores configurados en el `disableidSyncs` parámetro para la `getInstance` función. |
| Los iFrames de terceros no reciben ECID | Se ha corregido los ECID en la versión móvil de Safari, así como ECID que no funcionaban para distintos iFrames. |

