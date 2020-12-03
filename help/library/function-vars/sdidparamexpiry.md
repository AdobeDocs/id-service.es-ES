---
description: Esta configuración permite anular el intervalo de caducidad predeterminado de ID de datos suplementarios (SDID) al pasar ese ID de una página a otra mediante la función de ayuda appendSupplementalDataIDTo. De forma predeterminada, el código de servicio de ID de la página de recepción dispone de 30 segundos para obtener el SDID de la dirección URL que envía la página de referencia. Si el código de servicio de ID de la página de recepción no puede recuperar el SDID en menos de 30 segundos, solicita un nuevo SDID. Esta funcionalidad es principalmente para clientes de A4T que necesitan pasar el SDID de una página a otra y desean controlar este intervalo de tiempo de espera.
keywords: ID Service
seo-description: Esta configuración permite anular el intervalo de caducidad predeterminado de ID de datos suplementarios (SDID) al pasar ese ID de una página a otra mediante la función de ayuda appendSupplementalDataIDTo. De forma predeterminada, el código de servicio de ID de la página de recepción dispone de 30 segundos para obtener el SDID de la dirección URL que envía la página de referencia. Si el código de servicio de ID de la página de recepción no puede recuperar el SDID en menos de 30 segundos, solicita un nuevo SDID. Esta funcionalidad es principalmente para clientes de A4T que necesitan pasar el SDID de una página a otra y desean controlar este intervalo de tiempo de espera.
seo-title: sdidParamExpiry
title: sdidParamExpiry
uuid: cdaf7e2d-b196-4c70-936d-8a98191cbb85
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 9%

---


# sdidParamExpiry{#sdidparamexpiry}

Esta configuración permite anular el intervalo de caducidad predeterminado de ID de datos suplementarios (SDID) al pasar ese ID de una página a otra mediante la función de ayuda appendSupplementalDataIDTo. De forma predeterminada, el código de servicio de ID de la página de recepción dispone de 30 segundos para obtener el SDID de la dirección URL que envía la página de referencia. Si el código de servicio de ID de la página de recepción no puede recuperar el SDID en menos de 30 segundos, solicita un nuevo SDID. Esta funcionalidad es principalmente para clientes de A4T que necesitan pasar el SDID de una página a otra y desean controlar este intervalo de tiempo de espera.

**Anular el tiempo de espera SDID**

Si debe cambiar el tiempo de espera de SDID predeterminado, agregue `sdidParamExpiry` a la `Visitor.getInstance` función con la sintaxis siguiente:

**Sintaxis:**` sdidParamExpiry: *`tiempo en segundos`*`

**Ejemplo de código**

Cuando está configurado, el código de servicio de ID podría ser similar a este ejemplo. Este ejemplo establece el tiempo de espera SDID en 15 segundos. Esta configuración funciona con el  método de ayuda [appendSupplementalDataIDTo](../../library/get-set/appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d).

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

