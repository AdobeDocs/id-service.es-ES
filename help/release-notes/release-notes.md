---
description: Versiones de funciones, actualizaciones o cambios en el servicio de identidad de Experience Cloud.
keywords: Servicio de ID
seo-description: Versiones de funciones, actualizaciones o cambios en el servicio de identidad de Experience Cloud.
seo-title: Notas de la versión 2019
title: Notas de la versión 2019
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: tm+mt
source-git-commit: 4532d09cc9b4d83fa62c13bd1adac7abdae222b1

---


# Notas de la versión 2019 {#release-notes}

Versiones de funciones, actualizaciones o cambios en el servicio de identidad de Experience Cloud.

## Notas de la versión 2019 {#topic-1b9a1c3ec5044e1c987785950f697e25}

Versiones de características, actualizaciones o cambios en el servicio de ID de [!DNL Experience Cloud].

## Versión 4.4 {#version-4point4}

**Nueva función**

[SHA 256 Hash Support for setcustomerids](/help/reference/hashing-support.md). El servicio Experience Cloud ID (ECID) admite el algoritmo hash SHA -256 que le permite pasar ID de cliente o direcciones de correo electrónico y transferir ID hash.

**Correcciones, mejoras, mejoras**

* We made a configuration update to `cookieDomain`. The ECID library now filters out the empty string `cookieDomain` in `initConfig` and uses the top level cookie domain, which is returned by the getDomain method. (CORE-29223)
* We fixed a bug related to `getVisitorValues` in `localVisitor`. (CORE-31287)
* We fixed a bug where there was an inconsistency for the MCOPTOUT value in the Safari browser, returned by the `getVisitorValue` method. (CORE-29719)
* We updated the Opt-in library by adding `optIn.off` to unsubscribe from events.
* We fixed a bug related to the setTimeout function, where `setTimeout` violated the Content Security Policy (CSP) on some customer sites. (CORE-30623)

## Versión 4.3 {#version-4point3}

**Compatibilidad con ITP 2.1**. Si un servidor de seguimiento se configura en un CNAME de origen, se coloca una nueva cookie (s_ ecid) con el valor ECID. La biblioteca ECID hace referencia al valor para mantener el ID más allá de 7 días. See [ECID library methods in a Safari ITP world](/help/reference/ecid-library-methods.md).

**Corrección de errores para la configuración de securecookie.**

## Versión 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Servicio Opt-in**. La inclusión es una extensión del ID de Experience Cloud (ECID) que permite controlar si las bibliotecas de Experience Cloud pueden crear cookies en páginas web para visitantes (y luego cuáles). Using [Experience Platform Launch](https://docs.adobelaunch.com/), you can simplify gathering visitor opt-in consents for Experience Cloud solution by enabling Analytics, Target, Audience Manager, and other or all select Experience Cloud solutions to opt-in to your consent management system.

## Versión 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Elemento | Descripción |
|---|---|
| El indicador `disableIdSyncs` no funciona cuando se pasa una cadena | Solucionado. Ahora se aceptan los valores configurados en el `disableidSyncs` parámetro para la `getInstance` función. |
| Los iFrames de terceros no reciben ECID | Se ha corregido los ECID en la versión móvil de Safari, así como ECID que no funcionaban para distintos iFrames. |

