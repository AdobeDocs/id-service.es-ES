---
description: Esta configuración le permite sobrescribir el intervalo de caducidad predeterminado del ID de datos suplementarios (SDID) al pasar ese ID de una página a otra mediante la función de ayuda appendSupplementalDataIDTo. De forma predeterminada, el código de servicio de ID de la página de recepción tiene 30 segundos para obtener el SDID de la URL que envía la página de referencia. Si el código de servicio de ID de la página de recepción no puede recuperar el SDID en menos de 30 segundos, solicitará un nuevo SDID. Esta funcionalidad sirve principalmente para clientes de A4T que deben pasar el SDID de una página a otra y desean ejercer control sobre este intervalo de tiempo de espera.
keywords: Servicio de ID
seo-description: Esta configuración le permite sobrescribir el intervalo de caducidad predeterminado del ID de datos suplementarios (SDID) al pasar ese ID de una página a otra mediante la función de ayuda appendSupplementalDataIDTo. De forma predeterminada, el código de servicio de ID de la página de recepción tiene 30 segundos para obtener el SDID de la URL que envía la página de referencia. Si el código de servicio de ID de la página de recepción no puede recuperar el SDID en menos de 30 segundos, solicitará un nuevo SDID. Esta funcionalidad sirve principalmente para clientes de A4T que deben pasar el SDID de una página a otra y desean ejercer control sobre este intervalo de tiempo de espera.
seo-title: sdidParamExpiry
title: sdidParamExpiry
uuid: cdaf 7 e 2 d-b 196-4 c 70-936 d -8 a 98191 cbb 85
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# sdidParamExpiry{#sdidparamexpiry}

Esta configuración le permite sobrescribir el intervalo de caducidad predeterminado del ID de datos suplementarios (SDID) al pasar ese ID de una página a otra mediante la función de ayuda appendSupplementalDataIDTo. De forma predeterminada, el código de servicio de ID de la página de recepción tiene 30 segundos para obtener el SDID de la URL que envía la página de referencia. Si el código de servicio de ID de la página de recepción no puede recuperar el SDID en menos de 30 segundos, solicitará un nuevo SDID. Esta funcionalidad sirve principalmente para clientes de A4T que deben pasar el SDID de una página a otra y desean ejercer control sobre este intervalo de tiempo de espera.

**Sobrescribir el tiempo de espera de SDID**

Si debe cambiar el tiempo de espera de SDID predeterminado, agregue `sdidParamExpiry` a la función `Visitor.getInstance` con la sintaxis siguiente:

**Sintaxis:**` sdidParamExpiry: *`tiempo en segundos`*`

**Ejemplo de código**

Una vez configurado su código de servicio de ID, puede tener un aspecto similar al ejemplo siguiente. Este ejemplo establece el tiempo de espera de SDID en 15 segundos. Esta configuración funciona con el [método de ayuda appendSupplementalDataIDTo](../../mcvid-library/mcvid-get-set/mcvid-appendsupplementaldataidto.md#reference-65d09de6fde0418f8c62fa79304a755d).

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

