---
description: Versiones de funcionalidades, actualizaciones o cambios en el servicio de identidad de Experience Cloud.
keywords: ID Service
seo-description: Versiones de funcionalidades, actualizaciones o cambios en el servicio de Experience Cloud ID.
seo-title: Notas de la versión 2019
title: Notas de la versión 2019
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: tm+mt
source-git-commit: ba84c4dac9023ab13f5176c5665adbbdaeb00d33

---


# Notas de la versión 2019 {#release-notes}

Versiones de funcionalidades, actualizaciones o cambios en el servicio de Experience Cloud ID.

## Notas de la versión 2019 {#topic-1b9a1c3ec5044e1c987785950f697e25}

Versiones de características, actualizaciones o cambios en el servicio de ID de [!DNL Experience Cloud].

## Versión 4.4 {#version-4point4}

**Nueva función**

[SHA256 Soporte hash para setCustomerIDs](/help/reference/hashing-support.md). El servicio de identidad de Experience Cloud (ECID) es compatible con el algoritmo de hash SHA-256 que le permite pasar los ID de clientes o direcciones de correo electrónico, así como los ID de hash.

**Correcciones, mejoras**

* Hemos realizado una actualización de configuracióna`cookieDomain`. La biblioteca ECID ahora filtra la cadena vacía `cookieDomain` en `initConfig` y utiliza el dominio de cookie de primer nivel, que el método getDomain devuelve. (CORE-29223)
* Hemos corregido un error relacionado con `getVisitorValues` `localVisitor`. (CORE-31287)
* Hemos corregido un error en el que había una incoherencia para el valor MCOPTOUT en el explorador Safari, devuelto por el método `getVisitorValue`. (CORE-29719)
* Hemos actualizado la biblioteca de inclusión añadiendo `optIn.off` para cancelar la suscripción a eventos.
* Se ha corregido un error relacionado con la función setTimeout, donde `setTimeout` se infringía la Política de seguridad de contenido (PSC) en algunos sitios de clientes. (CORE-30623)

## Versión 4.3 {#version-4point3}

**Compatibilidad con ITP 2.1**. Si un servidor de seguimiento se configura en un CNAME de origen, se coloca una nueva cookie (s_ecid) con el valor ECID. La biblioteca ECID hace referencia al valor para mantener el ID más allá de 7 días. [Consulte métodos de biblioteca ECID en un entorno de Safari ITP](/help/reference/ecid-library-methods.md).

**Corrección de errores para la configuración de secureCookie.**

## Versión 4.1

Actualización `publishDestinations` por cambio de API nuevo. Con esta actualización, la información del referente de la página se puede exponer durante la sincronización de ID si lo desea. (CORE-23693)

## Versión 4.2

Compatibilidad con el complemento Audience Manager para IAB TCF, disponible mediante el objeto de inclusión ECID.

**Correcciones**

* IAB + OptIn no obtiene el MID para los clientes que vuelven a visitarlos (CORE-26022)
* Se ha corregido un error en la configuración de opt-in doOptInApply en la DTM (DTM-12958)
* La opción de exclusión ECID desactiva la sincronización de ID (CORE-23814)

## Versión 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Servicio Opt-in**. Opt-in es una extensión de Experience Cloud ID (ECID) que le permite controlar si las bibliotecas de Experience Cloud pueden crear cookies en las páginas web de los visitantes, y cuáles pueden hacerlo. Using [Experience Platform Launch](https://docs.adobelaunch.com/), you can simplify gathering visitor opt-in consents for Experience Cloud solution by enabling Analytics, Target, Audience Manager, and other or all select Experience Cloud solutions to opt-in to your consent management system.

## Versión 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Elemento | Descripción |
|---|---|
| El indicador`disableIdSyncs` no funciona cuando se pasa una cadena | Solucionado. Ahora se aceptan los valores configurados en el `disableidSyncs` parámetro para la `getInstance` función. |
| Los iFrames de terceros no reciben ECID | Se ha corregido los ECID en la versión móvil de Safari, así como ECID que no funcionaban para distintos iFrames. |

