---
description: Llame a esta función del servicio de ID para determinar si el servicio de ID ha generado un ID de visitante Experience Cloud (MID) del lado del cliente. Disponible en VisitorAPI.js versión 1.7.0 o posteriores.
keywords: Servicio de ID
seo-description: Llame a esta función del servicio de ID para determinar si el servicio de ID ha generado un ID de visitante Experience Cloud (MID) del lado del cliente. Disponible en VisitorAPI.js versión 1.7.0 o posteriores.
seo-title: isClientSideMarketingCloudVisitorID
title: isClientSideMarketingCloudVisitorID
uuid: 1c39ac60-1d2b-4ed4-a2ea-30d680e61e10
exl-id: ed2672e7-da1a-4c02-9f4e-c14419ec9ec7
translation-type: ht
source-git-commit: 4453ebf701ea2dc06e6093dd77be6eb0f3b2936e
workflow-type: ht
source-wordcount: '148'
ht-degree: 100%

---

# isClientSideMarketingCloudVisitorID {#isclientsidemarketingcloudvisitorid}

Llame a esta función del servicio de ID para determinar si el servicio de ID ha generado un ID de visitante Experience Cloud (MID) del lado del cliente. Disponible en VisitorAPI.js versión 1.7.0 o posteriores.

**Sintaxis**

`var *`variableName`* = visitor.isClientSideMarketingCloudVisitorID()`

En la tabla siguiente se enumeran y describen las respuestas que devuelve esta función.

<table id="table_5D08A5DD6FD04F94818B0E8B790D3136"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Respuesta </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> true</span> </p> </td> 
   <td colname="col2"> <p>El servicio de ID no pudo recibir o bien no recibió un MID desde el servidor de <span class="keyword">Experience Cloud</span>. Creó un MID de manera local, en el navegador (lado del cliente). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> false</span> </p> </td> 
   <td colname="col2"> <p>El servicio de ID recibió un MID del servidor de <span class="keyword">Experience Cloud</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> null</span> </p> </td> 
   <td colname="col2"> <p>El servicio de ID no realizó una llamada al servidor de <span class="keyword">Experience Cloud</span>. </p> </td> 
  </tr> 
 </tbody> 
</table>
