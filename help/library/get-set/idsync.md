---
description: Las funciones del servicio de ID idSyncByURL y idSyncByDataSource le permiten implementar manualmente una sincronización de ID en el iFrame de publicación de destino. Estas funciones están disponibles en VisitorAPI.js versión 1.10 o posteriores.
keywords: Servicio de ID
seo-description: Las funciones del servicio de ID idSyncByURL y idSyncByDataSource le permiten implementar manualmente una sincronización de ID en el iFrame de publicación de destino. Estas funciones están disponibles en VisitorAPI.js versión 1.10 o posteriores.
seo-title: Sincronización de ID por dirección URL o fuente de datos
title: Sincronización de ID por dirección URL o fuente de datos
uuid: ff83d910-8375-4295-9f2a-e14c15eee09a
translation-type: tm+mt
source-git-commit: e949edbd231b9c085d897153359b3cb442195888

---


# Sincronización de ID por dirección URL o fuente de datos{#id-synchronization-by-url-or-data-source}

Las funciones del servicio de ID idSyncByURL y idSyncByDataSource le permiten implementar manualmente una sincronización de ID en el iFrame de publicación de destino. Estas funciones están disponibles en VisitorAPI.js versión 1.10 o posteriores.

## Sintaxis, propiedades y macros {#section-90ac61617482463aaf4c57009b830332}

**Sintaxis**

<table id="table_ADC7501511914805A6A6B24B2DFEBA51"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Código </th> 
   <th colname="col2" class="entry"> Sincroniza los ID de los usuarios </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByURL(); </span> </p> </td> 
   <td colname="col2"> <p>Entre diferentes socios de datos y <span class="keyword">Audience Manager</span> mediante el uso de una URL de sincronización de ID personalizada. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <p> <span class="codeph"> visitor.idSyncByDataSource(); </span> </p> </td> 
   <td colname="col2"> <p>Cuando se conoce el DPID y el DPUUID, y se desea enviar a <span class="keyword">Audience Manager</span> en el formato estándar de URL de sincronización de ID. </p> <p> 
     <draft-comment>
       Cuando ya conoce el ID de usuario y desea enviarlo a Audience Manager. 
     </draft-comment> </p> </td> 
  </tr> 
 </tbody> 
</table>

**Propiedades**

En la tabla siguiente se enumeran y definen las propiedades disponibles para ambas funciones.

<table id="table_5343BE784E694C67B09A0A8878CF8001"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Nombre </th> 
   <th colname="col2" class="entry"> Tipo </th> 
   <th colname="col3" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> dpid </span> </td> 
   <td colname="col2"> Cadena </td> 
   <td colname="col3"> <p>ID de proveedor de datos asignado por Audience Manager. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> dpuuid </span> </td> 
   <td colname="col2"> Cadena </td> 
   <td colname="col3"> <p>El ID exclusivo de proveedor de datos para el usuario. </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> minutesToLive </span> </td> 
   <td colname="col2"> Número </td> 
   <td colname="col3"> <p> <i>(Opcional)</i> Establece el tiempo de caducidad de la cookie. Debe ser un número entero. El valor predeterminado es de 20160 minutos (14 días). </p> </td> 
  </tr> 
  <tr valign="top"> 
   <td colname="col1"> <span class="codeph"> url </span> </td> 
   <td colname="col2"> Cadena </td> 
   <td colname="col3"> <p>Dirección URL de destino. </p> </td> 
  </tr> 
 </tbody> 
</table>

**Macros**

Ambas funciones aceptan las siguientes macros:

* `%TIMESTAMP%`: genera una marca de hora (en milésimas de segundo). Se emplea para ignorar la caché.
* `%DID%`: inserta el ID de Audience Manager para el usuario.
* `%HTTP_PROTO%`: establece el protocolo de comunicación (`http` o `https`).

## Ejemplo de código y salida {#section-0115615c37584a19a2ab11e917c4e7e9}

Las dos funciones devuelven `Successfully queued` si se realiza correctamente. Si no, devuelven una cadena con un mensaje de error.

### visitor.idSyncByURL

**Código de ejemplo**

```javascript
   //Instatiate Visitor
    var visitor = Visitor.getInstance
    ("MARKETING-CLOUD-ORG-ID-HERE",{}); 
   // Fires url with macros replaced 
    visitor.idSyncByURL({ 
    dpid: '24', // must be a string 
    url: '//su.addthis.com/red/usync?pid=16&puid=%DID%&url=%HTTP_PROTO%://
    dpm.demdex.net/ibs:dpid=420&dpuuid={{uid}}', 
    minutesToLive: 20160 // optional, defaults to 20160 minutes (14 days) });
```

**Salida de ejemplo**

`http://su.addthis.com/red/usync?pid=16&puid=28777806459181003670799219185178493848&url=http%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D`

### visitor.idSyncByDataSource

**Código de ejemplo**

```javascript
  //Instantiate Visitor
   var visitor = Visitor.getInstance
   ("MARKETING-CLOUD-ORG-ID-HERE",{}); 
  // Fires 'http:/https:' + '//dpm.demdex.net/ibs:dpid=&dpuuid='
   visitor.idSyncByDataSource({ 
     dpid: '24', // must be a string
     dpuuid: '98765', // must be a string 
     minutesToLive: 20160 // optional, defaults to 20160 minutes (14 days) });
```

**Salida de ejemplo**

`http://dpm.demdex.net/ibs:dpid=24&dpuuid=98765`

>[!MORE_LIKE_THIS]
>
>* [DIL idSync](https://docs.adobe.com/content/help/en/audience-manager/user-guide/dil-api/dil-instance-methods.html#idsync)

