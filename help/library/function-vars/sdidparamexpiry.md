---
description: Esta configuración le permite anular el intervalo de caducidad predeterminado de ID de datos suplementarios (SDID) al pasar dicho identificador de una página a otra mediante la función de ayuda appendSupplementalDataIDTo. De forma predeterminada, el código del servicio de ID de visitante de la página receptora tiene 30 segundos para obtener el SDID de la URL que envía la página de referencia. Si el código de servicio de ID de visitante de la página receptora no puede recuperar el SDID en menos de 30 segundos, solicitará un SDID nuevo. Esta funcionalidad está destinada principalmente a los clientes de A4T que necesitan pasar el SDID de una página a otra y desean controlar este intervalo de tiempo de espera.
keywords: Servicio de ID de visitante
title: sdidParamExpiry
exl-id: 5458ffa5-03d1-4c52-907d-c50fe00ce35d
TQID: https://experienceleague.adobe.com/PUHy-KpWKY0BQSMkKidwpLYES6FvME2EtKCbCpfMFrw
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 266
ht-degree: 54%

---

# sdidParamExpiry{#sdidparamexpiry}

Esta configuración le permite anular el intervalo de caducidad predeterminado de ID de datos suplementarios (SDID) al pasar dicho identificador de una página a otra mediante la función de ayuda appendSupplementalDataIDTo. De forma predeterminada, el código del servicio de ID de visitante de la página receptora tiene 30 segundos para obtener el SDID de la URL que envía la página de referencia. Si el código de servicio de ID de visitante de la página receptora no puede recuperar el SDID en menos de 30 segundos, solicitará un SDID nuevo. Esta funcionalidad está destinada principalmente a los clientes de A4T que necesitan pasar el SDID de una página a otra y desean controlar este intervalo de tiempo de espera.

**Anulación del tiempo de espera de SDID**

Si debe cambiar el tiempo de espera de SDID predeterminado, agregue `sdidParamExpiry` a la `Visitor.getInstance` función con la sintaxis siguiente:

**Sintaxis:** `sdidParamExpiry: *`tiempo en segundos`*`

**Ejemplo de código**

Cuando se configura, el código del servicio de ID de visitante puede ser similar al de este ejemplo. Este ejemplo establece el tiempo de espera del SDID en 15 segundos. Esta configuración funciona con el método de ayuda [appendSupplementalDataIDTo](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d).

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   ... 
   //Change the default SDID timeout to 15 seconds 
   sdidParamExpiry: 15 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219"); 
```

