---
description: Versiones de funcionalidades, actualizaciones o cambios en el servicio de identidad de Experience Cloud.
keywords: Servicio de ID
title: Notas de la versión de 2021
exl-id: f0bbb100-49a9-4bba-8cee-5f40bec87984
source-git-commit: fcd3e8b65bb84e94eabac7ffec6a34f4cf75ec3d
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 100%

---

# Notas de la versión de Experience Cloud ID Service - 2021

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
