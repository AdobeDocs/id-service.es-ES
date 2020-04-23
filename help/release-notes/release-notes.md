---
description: Versiones de funcionalidades, actualizaciones o cambios en el servicio de identidad de Experience Cloud.
keywords: ID Service
seo-description: Versiones de funcionalidades, actualizaciones o cambios en el servicio de identidad de Experience Cloud.
seo-title: Notas de la versión 2020
title: Notas de la versión 2020
translation-type: ht
source-git-commit: c4da0f3da99a96d2be7421f49e0e88286d0505e0

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
