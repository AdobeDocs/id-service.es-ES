---
description: Se trata de una API asíncrona que devuelve identificadores para Analytics, el servicio de ID, la exclusión de la recopilación de datos, la ubicación geográfica y el contenido “blob” de metadatos de forma predeterminada. Además, se puede controlar cuáles son los ID que desea que se devuelvan con la enumeración opcional visitor.FIELDS.
keywords: Servicio de ID
seo-description: Se trata de una API asíncrona que devuelve identificadores para Analytics, el servicio de ID, la exclusión de la recopilación de datos, la ubicación geográfica y el contenido “blob” de metadatos de forma predeterminada. Además, se puede controlar cuáles son los ID que desea que se devuelvan con la enumeración opcional visitor.FIELDS.
seo-title: getVisitorValues
title: getVisitorValues
uuid: 7 fb 831 b 3-cf 7 e -40 e 2-a 219-07 fy 28 ad 49 c
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# getVisitorValues{#getvisitorvalues}

Se trata de una API asíncrona que devuelve identificadores para Analytics, el servicio de ID, la exclusión de la recopilación de datos, la ubicación geográfica y el contenido “blob” de metadatos de forma predeterminada. Además, se puede controlar cuáles son los ID que desea que se devuelvan con la enumeración opcional visitor.FIELDS.

Contenido:

<ul class="simplelist"> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-getvisitorvalues.md#section-5aebe3907b2b46e997f45a1d1ed35c09" format="dita" scope="local"> Sintaxis </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-getvisitorvalues.md#section-36a31683558742a5915db3a391e09f7b" format="dita" scope="local"> Caso de uso 1: Solicitar el conjunto de datos predeterminado </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-getvisitorvalues.md#section-467b2f4e513344c89b7332b05f6f59f3" format="dita" scope="local"> Caso de uso 2: Solicitar un conjunto de datos personalizado </a> </li> 
 <li> <a href="../../mcvid-library/mcvid-get-set/mcvid-getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5" format="dita" scope="local"> Parámetros de respuesta definidos </a> </li> 
</ul>

## Sintaxis {#section-5aebe3907b2b46e997f45a1d1ed35c09}

Esta función utiliza la siguiente sintaxis (la cursiva representa un marcador de posición para una variable): ` var *`Tipo`* = visitor.getVisitorValues (callback, [visitor.FIELDS. *`de ID de`*, visitor.FIELDS. *`valor Tipo de TYPEID`*]);`

En los parámetros de función:

* ` *`la llamada de retorno`*` representa su propio código de rellamada que recibe los ID devueltos.
* *(Opcional)* ` visitor.FIELDS. *`El tipo`*` de ID es una enum que permite especificar los [valores](../../mcvid-library/mcvid-get-set/mcvid-getvisitorvalues.md#section-4c4c300167694c6fbff1d6c612f372b5) de ID que desea que devuelvan esta función.

Consulte los casos de uso y definiciones siguientes para obtener más información.

## Caso de uso 1: Solicitar el conjunto de datos predeterminado {#section-36a31683558742a5915db3a391e09f7b}

Este código devuelve el conjunto de datos estándar. Su solicitud y respuesta pueden tener un aspecto similar al de los ejemplos siguientes.

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{...}); 
   
//Add your callback to the GET method to return IDs and data. 
visitor.getVisitorValues(visitorIdsCallback);
```

En la respuesta de ejemplo predeterminada, se han acortado algunos valores para realizar la demostración.

```js
//Formatted IDs in JSON response 
{ 
    MCMID: 'mid-1234', 
    MCOPTOUT: 'isoptedout-true', 
    MCAID: 'aid-1234', 
    MCAAMLH: 7, 
    MCAAMB: 'hgfe54236786oygj' 
}
```

## Caso de uso 2: Solicitar un conjunto de datos personalizado {#section-467b2f4e513344c89b7332b05f6f59f3}

Este código utiliza una matriz opcional para devolver un conjunto de ID específico mediante la enumeración `visitor.FIELDS`. En este caso, solo queremos el Experience Cloud ID (MCID) y el ID de Analytics (MCAID). Su solicitud y respuesta pueden tener un aspecto similar al de los ejemplos siguientes.

```js
//Call the ID service 
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here", { ... });

// Add an optional array to specify which IDs you want to return. 
visitor.getVisitorValues(visitorIdsCallback, [visitor.FIELDS.MCMID, visitor.FIELDS.MCAID]);
```

La respuesta de ejemplo personalizada devuelve solo los ID especificados en la solicitud.

```js
//Formatted IDs in JSON response 
{ 
    MCMID: 'mid-1234', 
    MCAID: 'aid-4321' 
}
```

## Parámetros de respuesta definidos {#section-4c4c300167694c6fbff1d6c612f372b5}

La tabla que se muestra a continuación enumera y define los parámetros de respuesta. Estos son también todos los valores de la enumeración `visitor.FIELDS`. Observe que este método devuelve una cadena vacía si no hay valores para una variable en concreto.

<table id="table_32D0FEEA76CE4F298EED4B8F5C644232"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Valor </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAAMB </span> </p> </td> 
   <td colname="col2"> <p>Metadatos de <span class="keyword">Audience Manager</span> cifrados conocidos como el "blob". </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAAMLH </span> </p> </td> 
   <td colname="col2"> <p>El ID de región de recopilación de datos. Se trata de un identificador numérico para la ubicación geográfica de un centro de datos de servicio de ID concreto. </p> <p>Consulte <a href="https://marketing.adobe.com/resources/help/en_US/aam/dcs-regions.html" format="https" scope="external"> ID de región DCS, Ubicaciones y Nombres </a> de host y <a href="../../mcvid-library/mcvid-get-set/mcvid-getlocationhint.md#reference-a761030ff06c4439946bb56febf42d4c" format="dita" scope="local"> getlocationhint </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCAID </span> </p> </td> 
   <td colname="col2"> <p>El ID de <span class="keyword">Analytics</span> del visitante. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCMID </span> </p> </td> 
   <td colname="col2"> <p>El Experience Cloud ID del visitante. </p> <p>Consulte la información relativa a las <a href="../../mcvid-introduction/mcvid-cookies.md" format="dita" scope="local">cookies y el servicio Experience Cloud ID </a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> MCOPTOUT </span> </p> </td> 
   <td colname="col2"> <p>Un indicador que indica si un visitante se ha excluido de la recopilación de datos. </p> <p>Los valores incluyen: </p> <p> 
     <ul id="ul_E82431DE12B449F8822499364B363798"> 
      <li id="li_2BAB7C15A38A408E8FC4B85E70B66E46"> <span class="codeph"> 'isoptedout-true'</span>: un visitante ha excluido la recopilación de datos. </li> 
      <li id="li_BB80AE4CEBC44166BC04428B212FEF51"> <span class="codeph"> 'isoptedout-false'</span>: un visitante no ha excluido la recopilación de datos. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

