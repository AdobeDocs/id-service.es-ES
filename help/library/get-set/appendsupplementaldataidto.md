---
description: Este método de ayuda le permite anexar el ID de datos adicionales (SDID) como un parámetro de cadena de consulta a una URL de redireccionamiento. Resulta útil al utilizar A4T y debe conservar el SDID de una página a otra y unir esas visitas independientes. Para utilizar esta función, debe haber implementado el servicio de ID con el mismo ID de organización en los dominios de origen y destino.
keywords: Servicio de ID
seo-description: Este método de ayuda le permite anexar el ID de datos adicionales (SDID) como un parámetro de cadena de consulta a una URL de redireccionamiento. Resulta útil al utilizar A4T y debe conservar el SDID de una página a otra y unir esas visitas independientes. Para utilizar esta función, debe haber implementado el servicio de ID con el mismo ID de organización en los dominios de origen y destino.
seo-title: appendSupplementalDataIDTo
title: appendSupplementalDataIDTo
uuid: f3504d82-8da3-4971-818b-3df57df4ec2d
translation-type: ht
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# appendSupplementalDataIDTo{#appendsupplementaldataidto}

Este método de ayuda le permite anexar el ID de datos adicionales (SDID) como un parámetro de cadena de consulta a una URL de redireccionamiento. Resulta útil al utilizar A4T y debe conservar el SDID de una página a otra y unir esas visitas independientes. Para utilizar esta función, debe haber implementado el servicio de ID con el mismo ID de organización en los dominios de origen y destino.

Contenido:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> Ejemplo de sintaxis y código </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4" format="dita" scope="local"> Salida de ejemplo </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> Ejemplo de sintaxis y código </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-99946715cefa4acc95200b093db5297e" format="dita" scope="local"> Modificación del tiempo de espera del SDID con sdidParamExpiry </a> </li> 
</ul>

## Ejemplo de sintaxis y código {#section-cbb0b2f73bcc418386796c24c01b2365}

**Sintaxis:** ` appendSupplementalDataIDTo( *`URL`*, *`SDID`*)`

**Ejemplo de código**

```js
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
   ... 
}); 
 
//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, "67987653465787219");
```

## Salida de ejemplo  {#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4}

Como se muestra a continuación, el redireccionamiento de URL contiene el SDID del visitante, su ID de organización y una marca de fecha y hora de UNIX en la llamada a la página de recepción.

<ul class="simplelist"> 
 <li> <span class="codeph"> www.domain.com/pageB?adobe_mc_sdid=SDID=123|MCORGID=123456789@AdobeOrg|TS=1498569322 </span> </li> 
</ul>

## Modificación del tiempo de espera del SDID con sdidParamExpiry {#section-99946715cefa4acc95200b093db5297e}

La configuración [sdidParamExpiry](../../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458) le permite sobrescribir el intervalo de caducidad predeterminado del ID de datos suplementarios (SDID) al pasar ese ID de una página a otra mediante la función de ayuda `appendSupplementalDataIDTo`. De forma predeterminada, el código de servicio de ID de la página de recepción tiene 30 segundos para obtener el SDID de la URL que envía la página de referencia. Si el código de servicio de ID de la página de recepción no puede recuperar el SDID en menos de 30 segundos, solicitará un nuevo SDID. Esta funcionalidad sirve principalmente para clientes de A4T que deben pasar el SDID de una página a otra y desean ejercer control sobre este intervalo de tiempo de espera.

Si debe cambiar el tiempo de espera de SDID predeterminado, agregue `sdidParamExpiry` a la `Visitor.getInstance` función con la sintaxis siguiente:

**Sintaxis:**` sdidParamExpiry: *`tiempo en segundos`*`

**Ejemplo de código**

Una vez configurado su código de servicio de ID, puede tener un aspecto parecido a este ejemplo. Este ejemplo establece el tiempo de espera de SDID en 15 segundos.

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

