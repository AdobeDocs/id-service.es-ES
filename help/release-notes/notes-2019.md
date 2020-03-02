---
description: Versiones de funcionalidades, actualizaciones o cambios en el servicio de identidad de Experience Cloud.
keywords: ID Service
seo-description: Versiones de funcionalidades, actualizaciones o cambios en el servicio de identidad de Experience Cloud.
seo-title: Notas de la versión 2019
title: Notas de la versión 2019
uuid: a5a59410-7f85-48f9-a30a-fef1c2e2b558
translation-type: ht
source-git-commit: 25a9af7a28462bc0bd26cf4a5a58203e76a83366

---


# Notas de la versión de Experience Cloud: 2019 {#release-notes}

Versiones de funcionalidades, actualizaciones o cambios en el servicio de identidad de Experience Cloud.

## Versión 4.4.1

Agregar casilla de verificación de aprobación previa a la inclusión para el análisis de medios en la extensión de Launch  de ECID (CORE-33185)

**Correcciones**

* Problema con el análisis de la cadena de entrada preOptInApprovals de la extensión de lanzamiento de ECID (CORE-34041)
* Disminución de rendimiento cuando se utiliza trackingServer (CORE-32387)

## Versión 4.4 {#version-4point4}

**Nueva función**

[SHA256 Soporte hash para setCustomerIDs](/help/reference/hashing-support.md). El servicio de Experience Cloud ID (ECID) es compatible con el algoritmo de hash SHA-256 que le permite pasar los ID de clientes o direcciones de correo electrónico, así como los ID de hash.

**Correcciones, mejoras**

* Hemos realizado una actualización de configuracióna `cookieDomain`. La biblioteca ECID ahora filtra la cadena vacía `cookieDomain` en `initConfig` y utiliza el dominio de cookie de primer nivel, que el método getDomain devuelve. (CORE-29223)
* Hemos corregido un error relacionado con `getVisitorValues` `localVisitor`. (CORE-31287)
* Hemos corregido un error en el que había una incoherencia para el valor MCOPTOUT en el explorador Safari, devuelto por el método `getVisitorValue`. (CORE-29719)
* Hemos actualizado la biblioteca de inclusión añadiendo `optIn.off` para cancelar la suscripción a eventos.
* Se ha corregido un error relacionado con la función setTimeout, donde `setTimeout` se infringía la Política de seguridad de contenido (PSC) en algunos sitios de clientes. (CORE-30623)

## Versión 4.3 {#version-4point3}

**Compatibilidad con ITP 2.1**. Si un servidor de seguimiento se configura en un CNAME de origen, se coloca una nueva cookie (s_ecid) con el valor ECID. La biblioteca ECID hace referencia al valor para mantener el ID más allá de 7 días. Consulte [métodos de biblioteca ECID en un entorno de Safari ITP](/help/reference/ecid-library-methods.md).

**Corrección de errores para la configuración de secureCookie.**

## Versión 4.1

Actualizar `publishDestinations` por cada cambio de API nuevo. Con esta actualización, la información del referente de la página se puede exponer durante la sincronización de ID si lo desea. (CORE-23693)

## Versión 4.2

Compatibilidad con el complemento de Audience Manager para IAB TCF, disponible a través del objeto de inclusión ECID.

**Correcciones**

* Error de IAB + OptIn al obtener el MID para los clientes que vuelven a visitar (CORE-26022)
* Se ha corregido un error en la configuración de inclusión doesOptInApply en la DTM (DTM-12958)
* La opción de exclusión de ECID desactiva la sincronización de ID (CORE-23814)

## Versión 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Servicio Opt-in**. Opt-in es una extensión de Experience Cloud ID (ECID) que le permite controlar si las bibliotecas de Experience Cloud pueden crear cookies en las páginas web de los visitantes, y cuáles pueden hacerlo. Con [Experience Platform Launch](https://docs.adobe.com/content/help/es-ES/launch/using/overview.html), puede simplificar la recopilación de consentimientos de inclusión de los visitantes para la solución de Experience Cloud. Habilite Analytics, Target, Audience Manager y otras soluciones de Experience Cloud (o todas) para permitir su inclusión en un sistema de administración de consentimientos.

## Versión 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Elemento | Descripción |
|---|---|
| El indicador `disableIdSyncs` no funciona cuando se pasa una cadena. | Solucionado. Ahora se aceptan los valores configurados en el `disableidSyncs` parámetro para la `getInstance` función. |
| Los iFrames de terceros no reciben ECID | Se ha corregido los ECID en la versión móvil de Safari, así como ECID que no funcionaban para distintos iFrames. |
