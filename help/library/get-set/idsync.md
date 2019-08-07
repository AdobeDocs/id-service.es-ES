---
description: Las funciones del servicio de ID idSyncByURL y idSyncByDataSource le permiten implementar manualmente una sincronización de ID en el iFrame de publicación de destino. Estas funciones están disponibles en VisitorAPI.js versión 1.10 o posteriores.
keywords: Servicio de ID
seo-description: Las funciones del servicio de ID idSyncByURL y idSyncByDataSource le permiten implementar manualmente una sincronización de ID en el iFrame de publicación de destino. Estas funciones están disponibles en VisitorAPI.js versión 1.10 o posteriores.
seo-title: Sincronización de ID por dirección URL o fuente de datos
title: Sincronización de ID por dirección URL o fuente de datos
uuid: ff83d910-8375-4295-9f2a-e14c15eee09a
translation-type: tm+mt
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# Sincronización de ID por dirección URL o fuente de datos{#id-synchronization-by-url-or-data-source}

Las funciones del servicio de ID idSyncByURL y idSyncByDataSource le permiten implementar manualmente una sincronización de ID en el iFrame de publicación de destino. Estas funciones están disponibles en VisitorAPI.js versión 1.10 o posteriores.

Contenido:

<ul class="simplelist"> 
 <li> <a href="../../library/get-set/idsync.md#section-90ac61617482463aaf4c57009b830332" format="dita" scope="local"> Sintaxis, propiedades y macros </a> </li> 
 <li> <a href="../../library/get-set/idsync.md#section-0115615c37584a19a2ab11e917c4e7e9" format="dita" scope="local"> Ejemplo de código y salida </a> </li> 
</ul>

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
   <td colname="col2"> <p>Entre diferentes socios de datos y <span class="keyword">Audience Manager</span> mediante el uso de una URL de sincronización de ID personalizada. </p> <p> 
     <draft-comment>
       Entre diferentes socios de datos y Audience Manager. Por ejemplo, el socio x utilizaría esto para sincronizar un ID de usuario con un socio y enviarlo a Audience Manager. 
     </draft-comment> </p> </td> 
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
* `%HTTP_PROTO%`: Establece el protocolo de comunicación (`http` o `https`).

## Ejemplo de código y salida {#section-0115615c37584a19a2ab11e917c4e7e9}

Las dos funciones devuelven `Successfully queued` si se realiza correctamente. Si no, devuelven una cadena con un mensaje de error.

**visitor.idSyncByURL**

<table id="table_56AD8291DF9445C69CC2BF50435E1626"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Código de ejemplo </th> 
   <th colname="col2" class="entry"> Salida de ejemplo </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <code class="syntax javascript"> //Instatiate Visitor 
      var visitor = Visitor.getInstance("MARKETING-CLOUD-ORG-ID-HERE",{});

    //&amp;nbsp;Fires&amp;nbsp;url&amp;nbsp;with&amp;nbsp;macros&amp;nbsp;replaced
    visitor.idSyncByURL({
    &amp;nbsp;dpid:&amp;nbsp;'24',&amp;nbsp;//&amp;nbsp;must&amp;nbsp;be&amp;nbsp;a&amp;nbsp;string
    &amp;nbsp;url:&amp;nbsp;'//su.addthis.com/red/usync?pid=16&amp;amp;puid=%DID%&amp;amp;url=%HTTP_PROTO%%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D',
    &amp;nbsp;minutesToLive:&amp;nbsp;20160&amp;nbsp;//&amp;nbsp;optional,&amp;nbsp;defaults&amp;nbsp;to&amp;nbsp;20160&amp;nbsp;minutes&amp;nbsp;(14&amp;nbsp;days)&amp;nbsp;
    }); &lt;/code&gt; &lt;/p&gt; &lt;/td&gt;
<td colname="col2"> <p> <span class="codeph"> http://su.addthis.com/red/usync?pid=16&amp;puid=28777806459181003670799219185178493848&amp;url=http%3A%2F%2Fdpm.demdex.net%2Fibs%3Adpid%3D420%26dpuuid%3D%7B%7Buid%7D%7D </span> </p> </td> 
  </tr> 
 </tbody> 
</table>

**visitor.idSyncByDataSource**

<table id="table_90D61A7E715D47238AAFF2808B33C2F0"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Código de ejemplo </th> 
   <th colname="col2" class="entry"> Salida de ejemplo </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <code class="syntax javascript"> //Instantiate Visitor 
      var visitor = Visitor.getInstance("MARKETING-CLOUD-ORG-ID-HERE",{});

    //&amp;nbsp;Fires&amp;nbsp;'http:/https:'&amp;nbsp;+&amp;nbsp;'//dpm.demdex.net/ibs:dpid=&amp;lt;dpid&amp;gt;&amp;amp;dpuuid=&amp;lt;dpuuid&amp;gt;'
    visitor.idSyncByDataSource({
    &amp;nbsp;dpid:&amp;nbsp;'24',&amp;nbsp;//&amp;nbsp;must&amp;nbsp;be&amp;nbsp;a&amp;nbsp;string
    &amp;nbsp;dpuuid:&amp;nbsp;'98765',&amp;nbsp;//&amp;nbsp;must&amp;nbsp;be&amp;nbsp;a&amp;nbsp;string
    &amp;nbsp;minutesToLive:&amp;nbsp;20160&amp;nbsp;//&amp;nbsp;optional,&amp;nbsp;defaults&amp;nbsp;to&amp;nbsp;20160&amp;nbsp;minutes&amp;nbsp;(14&amp;nbsp;days)&amp;nbsp;
    }); &lt;/code&gt; &lt;/p&gt; &lt;/td&gt;
<td colname="col2"> <p> <span class="codeph"> http://dpm.demdex.net/ibs:dpid=24&amp;dpuuid=98765 </span> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!MORE_LIKE_THIS]
>
>* [DIL idSync](https://marketing.adobe.com/resources/help/en_US/aam/r_dil_idsync.html)

