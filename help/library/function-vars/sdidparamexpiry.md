---
description: Esta configuración le permite anular el intervalo de caducidad predeterminado de ID de datos suplementarios (SDID) al pasar dicho identificador de una página a otra mediante la función de ayuda appendSupplementalDataIDTo. De forma predeterminada, el código de servicio de ID de la página de recepción tiene 30 segundos para obtener el SDID de la URL que envía la página de referencia. Si el código de servicio de ID de la página receptora no puede recuperar el SDID en menos de 30 segundos, solicitará un nuevo SDID. Esta funcionalidad está destinada principalmente a los clientes de A4T que necesitan pasar el SDID de una página a otra y desean controlar este intervalo de tiempo de espera.
keywords: Servicio de ID
seo-description: Esta configuración le permite anular el intervalo de caducidad predeterminado de ID de datos suplementarios (SDID) al pasar dicho identificador de una página a otra mediante la función de ayuda appendSupplementalDataIDTo. De forma predeterminada, el código de servicio de ID de la página de recepción tiene 30 segundos para obtener el SDID de la URL que envía la página de referencia. Si el código de servicio de ID de la página receptora no puede recuperar el SDID en menos de 30 segundos, solicitará un nuevo SDID. Esta funcionalidad está destinada principalmente a los clientes de A4T que necesitan pasar el SDID de una página a otra y desean controlar este intervalo de tiempo de espera.
seo-title: sdidParamExpiry
title: sdidParamExpiry
uuid: cdaf7e2d-b196-4c70-936d-8a98191cbb85
exl-id: 5458ffa5-03d1-4c52-907d-c50fe00ce35d
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '357'
ht-degree: 100%

---

# sdidParamExpiry {#sdidparamexpiry}

Esta configuración le permite anular el intervalo de caducidad predeterminado de ID de datos suplementarios (SDID) al pasar dicho identificador de una página a otra mediante la función de ayuda appendSupplementalDataIDTo. De forma predeterminada, el código de servicio de ID de la página de recepción tiene 30 segundos para obtener el SDID de la URL que envía la página de referencia. Si el código de servicio de ID de la página receptora no puede recuperar el SDID en menos de 30 segundos, solicitará un nuevo SDID. Esta funcionalidad está destinada principalmente a los clientes de A4T que necesitan pasar el SDID de una página a otra y desean controlar este intervalo de tiempo de espera.

**Anulación del tiempo de espera de SDID**

Si debe cambiar el tiempo de espera de SDID predeterminado, agregue `sdidParamExpiry` a la `Visitor.getInstance` función con la sintaxis siguiente:

**Sintaxis:** ` sdidParamExpiry: *`tiempo en segundos`*`

**Ejemplo de código**

Cuando se configura, el código del servicio de ID puede tener un aspecto similar al de este ejemplo. Este ejemplo establece el tiempo de espera del SDID en 15 segundos. Esta configuración funciona con el  método de ayuda [appendSupplementalDataIDTo](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d).

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
   //Change the default SDID timeout to 15 seconds 
   sdidParamExpiry: 15 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219"); 
```
