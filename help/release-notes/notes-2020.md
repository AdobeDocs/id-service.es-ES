---
description: Versiones de funcionalidades, actualizaciones o cambios en el servicio de identidad de Experience Cloud.
keywords: Servicio de ID
title: Notas de la versión de 2020
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
source-git-commit: dce2c0036f697507381d0763c2f6a9538155681c
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 99%

---

# Notas de la versión de Experience Cloud - 2020 {#release-notes}

Versiones de funcionalidades, actualizaciones o cambios en el servicio de identidad de Experience Cloud.

## Versión 5.1.1

* Corrección de parches para configurar la cookie AMCV con `SameSite=None` cuando VisitorJS se carga en un iFrame.

## Versión 5.1.0

* Añadir la configuración de `sameSiteCookie` para especificar el `SameSite`atributo de la cookie AMCV. Esta configuración admite los siguientes valores para el atributo `SameSite`:
   * `Strict`
   * `Lax`
   * `None`

Para obtener más información sobre estos valores de atributo, visite [web.dev](https://web.dev/samesite-cookies-explained/) y [Actualizaciones de SameSite por los proyectos de Chromium](https://www.chromium.org/updates/same-site/).

## Versión 5.0.1

* Corrección de parches para `d_cf` se marca cuando se envía una nueva cadena de consentimiento IAB a los perímetros de recopilación de datos de Adobe.

## Versión 5.0.0

* Versión de visitante 5.0.0 compatible con `IAB 2.0`.

## Versión 4.6

* Marcar `loadSSL` como activo de forma predeterminada. Todas las llamadas al servicio de identidad estarán en `https` de forma predeterminada.  Los clientes pueden configurarlo como False si desean llamar a los servicios de identidad en un protocolo http desde las `non-ssl` páginas.
* Se ha actualizado la función utilizada para detectar la versión de `Internet-Explorer (IE)`, con el fin de corregir un problema del que informó `ESLint`.
Se corrigió un problema de rendimiento en `Internet-Explorer (IE) 11` cuando ECID recibe la `pre-approval` de optIn y se actualiza más tarde.

## Versión 4.5

* A partir de la versión 4.5, ECID rechazará cualquier ID vacío enviado al método de `setCustomerIDs`.
* Se ha corregido un problema que se producía cuando la opción de activación no se configuraba como `doesOptInApply=false` y `isIabContext=true`.

Consulte las [notas de la versión del Experience Cloud](https://experienceleague.adobe.com/docs/release-notes/experience-cloud/current.html?lang=es) para ver las notas de revisión mensuales de todos los productos.
