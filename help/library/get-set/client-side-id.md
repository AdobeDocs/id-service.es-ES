---
description: Llame a esta función del servicio de ID de visitante para determinar si el servicio de ID de visitante ha generado un ECID (MID) del lado del cliente. Disponible en VisitorAPI.js versión 1.7.0 o posteriores.
keywords: Servicio de ID de visitante
title: isClientSideMarketingCloudVisitorID
exl-id: ed2672e7-da1a-4c02-9f4e-c14419ec9ec7
TQID: https://experienceleague.adobe.com/kQK7Lw-j33luPqTSzQKGuf8fMPuOEDoQBzesZa-bvVo
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 128
ht-degree: 32%

---

# isClientSideMarketingCloudVisitorID{#isclientsidemarketingcloudvisitorid}

Llame a esta función del servicio de ID de visitante para determinar si el servicio de ID de visitante ha generado un ECID (MID) del lado del cliente. Disponible en `VisitorAPI.js` versión 1.7.0 o superior.

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
   <td colname="col2"> <p>El servicio de ID de visitante no pudo recibir o bien no recibió un MID desde el servidor de CX Enterprise. Creó un MID de manera local, en el navegador (lado del cliente). </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> false</span> </p> </td> 
   <td colname="col2"> <p>El servicio de ID de visitante recibió un MID del servidor de CX Enterprise. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> null</span> </p> </td> 
   <td colname="col2"> <p>El servicio de ID de visitante no realizó una llamada al servidor de CX Enterprise. </p> </td> 
  </tr> 
 </tbody> 
</table>

