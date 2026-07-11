---
description: Este método auxiliar permite agregar el ID de datos adicionales (SDID) como parámetro de cadena de consulta a una URL de redirección. Esto resulta útil cuando se utiliza A4T y es necesario mantener el SDID de una página a otra y unir esas visitas independientes. Para utilizar esta función, debe haber implementado el servicio de ID de visitante con el mismo ID de organización de IMS en los dominios de origen y destino.
keywords: Servicio de ID de visitante
title: appendSupplementalDataIDTo
exl-id: 7f0e7fca-4551-4165-a12b-c7e5514d6818
TQID: https://experienceleague.adobe.com/oR2LCiVk5N-Xnt3wTOKMt7UYFXzwEGFwJpKoz-ikzh8
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 354
ht-degree: 61%

---

# appendSupplementalDataIDTo{#appendsupplementaldataidto}

Este método auxiliar permite agregar el ID de datos adicionales (SDID) como parámetro de cadena de consulta a una URL de redirección. Esto resulta útil cuando se utiliza A4T y es necesario mantener el SDID de una página a otra y unir esas visitas independientes. Para utilizar esta función, debe haber implementado el servicio de ID de visitante con el mismo ID de organización de IMS en los dominios de origen y destino.

Contenido:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> Ejemplo de sintaxis y código </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4" format="dita" scope="local"> Salida de ejemplo </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-cbb0b2f73bcc418386796c24c01b2365" format="dita" scope="local"> Ejemplo de sintaxis y código </a> </li> 
 <li> <a href="../../library/get-set/appendsupplementaldataidto.md#section-99946715cefa4acc95200b093db5297e" format="dita" scope="local"> Modificación del tiempo de espera del SDID con sdidParamExpiry </a> </li> 
</ul>

## Ejemplo de sintaxis y código {#section-cbb0b2f73bcc418386796c24c01b2365}

**Sintaxis:** `appendSupplementalDataIDTo( *`URL`*, *`SDID`*)`

**Ejemplo de código**

```js
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE"); 

//Get current supplemental data id
var theCurrentSDID = visitor._supplementalDataIDCurrent ? visitor._supplementalDataIDCurrent : "";

//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, theCurrentSDID));
```

## Salida de ejemplo {#section-dbe02d7ff6bd4ad1a2a26bf9cff54fa4}

Como se muestra a continuación, el redireccionamiento de URL contiene el SDID del visitante, su ID de organización de IMS y una marca de tiempo de UNIX en la llamada a la página de recepción.

<ul class="simplelist"> 
 <li> <span class="codeph"> www.domain.com/pageB?adobe_mc_sdid=SDID=7996F0B028999505-13DA591039D6226|MCORGID=123456789@AdobeOrg|TS=1498569322 </span> </li> 
</ul>

## Modificación del tiempo de espera del SDID con sdidParamExpiry {#section-99946715cefa4acc95200b093db5297e}

La configuración [sdidParamExpiry](../../library/function-vars/sdidparamexpiry.md#reference-cef3fd03c43b4772b2422e220b40a458) le permite sobrescribir el intervalo de caducidad predeterminado del ID de datos suplementarios (SDID) al pasar ese ID de una página a otra mediante la función de ayuda `appendSupplementalDataIDTo`. De forma predeterminada, el código del servicio de ID de visitante de la página receptora tiene 30 segundos para obtener el SDID de la URL que envía la página de referencia. Si el código de servicio de ID de visitante de la página receptora no puede recuperar el SDID en menos de 30 segundos, solicitará un SDID nuevo. Esta funcionalidad está destinada principalmente a los clientes de A4T que necesitan pasar el SDID de una página a otra y desean controlar este intervalo de tiempo de espera.

Si debe cambiar el tiempo de espera de SDID predeterminado, agregue `sdidParamExpiry` a la `Visitor.getInstance` función con la sintaxis siguiente:

**Sintaxis:** `sdidParamExpiry: *`tiempo en segundos`*`

**Ejemplo de código**

Cuando se configura, el código del servicio de ID de visitante puede ser similar al de este ejemplo. Este ejemplo establece el tiempo de espera del SDID en 15 segundos.

```js
var visitor = Visitor.getInstance ("INSERT-IMS-ORG-ID-HERE",{ 
   ... 
   //Change the default SDID timeout to 15 seconds 
   sdidParamExpiry: 15 
}); 
 
//Get current supplemental data id
var theCurrentSDID = visitor._supplementalDataIDCurrent ? visitor._supplementalDataIDCurrent : "";

//Call helper method to append SDID to the Page B URL from Page A 
var pageB = "www.domain.com/pageB"; 
var pageBWithSdid = visitor.appendSupplementalDataIDTo(pageB, theCurrentSDID)); 
```

