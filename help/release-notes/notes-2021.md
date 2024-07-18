---
description: Versiones de funcionalidades, actualizaciones o cambios en el servicio de identidad de Experience Cloud.
keywords: Servicio de ID
title: Notas de la versión de 2021
exl-id: 56bffb6f-a4fc-40df-8bb2-17e43772fe60
source-git-commit: 52956b38c59f60507aaf236b152ce41fc1229d14
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 100%

---

# Notas de la versión del servicio de identidad de Experience Cloud - 2021

Versiones de funcionalidades, actualizaciones o cambios en el servicio de identidad de Experience Cloud.

## Visitante 5.3.0

En la versión de Visitor 5.3.0 se incluyeron las siguientes actualizaciones:

* Se ha actualizado el algoritmo para generar ECID local.
* Última inclusión con `Secure` y `SameSite` indicadores de cookie de privacidad.
* Corrección de parches para un problema con el explorador Firefox cuando una página se carga en un iFrame secundario.

## Visitante 5.2.0

En la versión de Visitor 5.2.0 se incluyeron las siguientes actualizaciones:

* Esta versión introduce un evento `onReceiveEcid`, que se llama cuando se recibe un ECID desde el servicio de identidad. Por ejemplo:

```js
visitorInstance.onReceiveEcid(callback(ecid){
 console.log(ecid)
})
```
