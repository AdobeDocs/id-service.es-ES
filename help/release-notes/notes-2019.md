---
description: Versiones de funcionalidades, actualizaciones o cambios en el servicio de Experience Cloud ID.
keywords: Servicio de ID
title: Notas de la versión 2019
exl-id: 11439e27-9740-4afc-a2b8-5e35d179f34f
source-git-commit: 503683b66b6022b7c1fecbfb197fe17e05ae9c64
workflow-type: ht
source-wordcount: '415'
ht-degree: 100%

---

# Notas de la versión de Experience Cloud - 2019 {#release-notes}

Versiones de funcionalidades, actualizaciones o cambios en el servicio de Experience Cloud ID.

## Versión 4.4.1

Agregar casilla de verificación de aprobación previa a la inclusión para el análisis de medios en la extensión de Launch de ECID.

**Correcciones**

* Problema con el análisis de la cadena de entrada preOptInApprovals de la extensión de lanzamiento de ECID.
* Disminución de rendimiento cuando se utiliza trackingServer.

## Versión 4.4 {#version-4point4}

**Nueva función**

[SHA256 Soporte hash para setCustomerIDs](/help/reference/hashing-support.md). El servicio de Experience Cloud ID (ECID) es compatible con el algoritmo de hash SHA-256 que le permite pasar los ID de clientes o direcciones de correo electrónico, así como los ID de hash.

**Correcciones, mejoras**

* Hemos realizado una actualización de configuracióna `cookieDomain`. La biblioteca ECID ahora filtra la cadena vacía `cookieDomain` en `initConfig` y utiliza el dominio de cookie de primer nivel, que el método getDomain devuelve.
* Hemos corregido un error relacionado con `getVisitorValues` en `localVisitor`.
* Hemos corregido un error en el que había una incoherencia para el valor MCOPTOUT en el explorador Safari, devuelto por el método `getVisitorValue`.
* Hemos actualizado la biblioteca de inclusión añadiendo `optIn.off` para cancelar la suscripción a eventos.
* Se ha corregido un error relacionado con la función setTimeout, donde `setTimeout` se infringía la Política de seguridad de contenido (PSC) en algunos sitios de clientes.

## Versión 4.3 {#version-4point3}

**Compatibilidad con ITP 2.1**. Si un servidor de seguimiento se configura en un CNAME de origen, se coloca una nueva cookie (s_ecid) con el valor ECID. La biblioteca ECID hace referencia al valor para mantener el ID más allá de 7 días. Consulte [métodos de biblioteca ECID en un entorno de Safari ITP](/help/reference/ecid-library-methods.md).

**Corrección de errores para la configuración de secureCookie.**

## Versión 4.1

Actualizar `publishDestinations` por cada cambio de API nuevo. Con esta actualización, la información del referente de la página se puede exponer durante la sincronización de ID si lo desea.

## Versión 4.2

Compatibilidad con el complemento de Audience Manager para IAB TCF, disponible a través del objeto de inclusión ECID.

**Correcciones**

* Error de IAB + OptIn al obtener el MID para los clientes que vuelven a visitar.
* Se ha corregido un error en la configuración de inclusión doesOptInApply en la DTM.
* La opción de exclusión de ECID desactiva la sincronización de ID.

## Versión 4.0 {#section-51a4be943bbe41558f196ef2654513e2}

**Servicio de inclusión (Opt-in)**. Opt-in es una extensión de Experience Cloud ID (ECID) que le permite controlar si las bibliotecas de Experience Cloud pueden crear cookies en las páginas web de los visitantes, y cuáles pueden hacerlo. Con [Experience Platform Launch](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=es), puede simplificar la recopilación de consentimientos de inclusión de los visitantes para la solución de Experience Cloud. Habilite Analytics, Target, Audience Manager y otras soluciones de Experience Cloud (o todas) para permitir su inclusión en un sistema de administración de consentimientos.

## Versión 3.4 {#section-046ce29b43af47cc849d4091098f5927}

| Elemento | Descripción |
|---|---|
| El indicador `disableIdSyncs` no funciona cuando se pasa una cadena. | Solucionado. Ahora se aceptan los valores configurados en el `disableidSyncs` parámetro para la `getInstance` función. |
| Los iFrames de terceros no reciben ECID | Se ha corregido el ECID en Safari Mobile y los ECID en varios iFrames que no funcionaban. |
