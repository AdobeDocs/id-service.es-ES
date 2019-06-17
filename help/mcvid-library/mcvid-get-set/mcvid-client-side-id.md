---
description: Llame a esta función del servicio de ID para determinar si el servicio de ID generó un ID de visitante de Experience Cloud (MID) del lado del cliente. Disponible en VisitorAPI.js versión 1.7.0 o posteriores.
keywords: Servicio de ID
seo-description: Llame a esta función del servicio de ID para determinar si el servicio de ID generó un ID de visitante de Experience Cloud (MID) del lado del cliente. Disponible en VisitorAPI.js versión 1.7.0 o posteriores.
seo-title: isClientSideMarketingCloudVisitorID
title: isClientSideMarketingCloudVisitorID
uuid: 1 c 39 ac 60-1 d 2 b -4 ed 4-a 2 ea -30 d 680 e 61 e 10
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}

Llame a esta función del servicio de ID para determinar si el servicio de ID generó un ID de visitante de Experience Cloud (MID) del lado del cliente. Disponible en VisitorAPI.js versión 1.7.0 o posteriores.

**Sintaxis**

`var *`variableName`* = visitor.isClientSideMarketingCloudVisitorID()`

La tabla siguiente enumera y describe las respuestas que devuelve esta función.

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

