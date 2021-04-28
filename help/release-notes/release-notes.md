---
description: Versiones de funcionalidades, actualizaciones o cambios en el servicio de Experience Cloud ID.
keywords: Servicio de ID
seo-description: Versiones de funcionalidades, actualizaciones o cambios en el servicio de Experience Cloud ID.
seo-title: Notas de la versión 2020
title: Notas de la versión 2020
exl-id: c9d7876e-debc-4c8e-8ebc-91646610c876
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '147'
ht-degree: 100%

---

# Notas de la versión de Experience Cloud: 2020 {#release-notes}

Versiones de funcionalidades, actualizaciones o cambios en el servicio de identidad de Experience Cloud (ECID).

## Versión 4.6

* Marcar `loadSSL` como activo de forma predeterminada. Todas las llamadas al servicio de identidad estarán en `https` de forma predeterminada.  Los clientes pueden configurarlo como False si desean llamar a los servicios de identidad en un protocolo http desde las `non-ssl` páginas.
* Se ha actualizado la función utilizada para detectar la versión de `Internet-Explorer (IE)`, con el fin de corregir un problema del que informó `ESLint`.
Se corrigió un problema de rendimiento en `Internet-Explorer (IE) 11` cuando ECID recibe la `pre-approval` de optIn y se actualiza más tarde.

## Versión 4.5

* A partir de la versión 4.5, ECID rechazará cualquier ID vacío enviado al método de `setCustomerIDs`.
* Se ha corregido un problema que se producía cuando la opción de activación no se configuraba como `doesOptInApply=false` y `isIabContext=true`.

Consulte las [notas de la versión del Experience Cloud](https://docs.adobe.com/content/help/es-ES/release-notes/experience-cloud/current.html) para ver las notas de revisión mensuales de todos los productos.
