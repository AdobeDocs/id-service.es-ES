---
description: Versiones de funcionalidades, actualizaciones o cambios en el servicio de identidad de Experience Cloud.
keywords: Servicio de ID
title: Notas de la versión 2021
source-git-commit: dce2c0036f697507381d0763c2f6a9538155681c
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 25%

---

# Notas de la versión del servicio de identidad de Experience Cloud - 2021

Versiones de funcionalidades, actualizaciones o cambios en el servicio de Experience Cloud ID.

## Visitante 5.3.0

En la versión de Visitor 5.3.0 se incluyeron las siguientes actualizaciones:

* Se ha actualizado el algoritmo para generar ECID local.
* Última inclusión con `Secure` y `SameSite` indicadores de cookie de privacidad.
* Corrección de parches para un problema con el explorador Firefox cuando una página se carga en un iFrame secundario.

## Visitante 5.2.0

En la versión de Visitor 5.2.0 se incluyeron las siguientes actualizaciones:

* Esta versión introduce un evento `onRecieveEcid`, que se llama cuando se recibe un ECID desde el servicio de identidad. Por ejemplo:

```js
visitorInstance.onRecieveEcid(callback(ecid){
 console.log(ecid)
})
```
