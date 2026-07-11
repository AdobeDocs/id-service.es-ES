---
description: Llame a estas funciones del servicio de ID de visitante para determinar el estado de tiempo de espera de una solicitud de ID del servicio de ID de visitante, Analytics o de Audience Manager. Disponible en VisitorAPI.js versión 1.7.0 o posteriores.
keywords: Servicio de ID de visitante
title: Métodos callTimeOut
exl-id: ff3a2c5e-a0a8-4257-b538-0e4ce454b4e8
TQID: https://experienceleague.adobe.com/DIis78iaPQ7qpawlKwWCwReXbh5Mt0K8J3w-5KYdhmg
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 129
ht-degree: 31%

---

# Métodos callTimeOut{#calltimeout-methods}

Llame a estas funciones del servicio de ID de visitante para determinar el estado de tiempo de espera de una solicitud de ID del servicio de ID de visitante, Analytics o de Audience Manager. Disponible en `VisitorAPI.js` versión 1.7.0 o superior.

## Funciones de tiempo de espera {#section-e08228ef5f9b45c9a84139bbb763164a}

<table id="table_B3ACE584B3224D838070D32A8462EF28"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Solución o servicio </th> 
   <th colname="col2" class="entry"> Sintaxis de funciones </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Servicio de ID de visitante </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.MCIDCallTimedOut()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword">Analytics</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.AnalyticsIDCallTimedOut()</span> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="keyword"> Audience Manager</span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">var <span class="varname"> variableName</span> = visitor.AAMIDCallTimedOut()</span> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Respuestas de función {#section-ff73aaca58b74e10a0953c49a3387160}

<table id="table_5D08A5DD6FD04F94818B0E8B790D3136"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Respuesta </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> TRUE</span> </p> </td> 
   <td colname="col2"> <p>El servicio de ID de visitante envió una solicitud y esta alcanzó su tiempo de espera máximo. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> FALSE</span> </p> </td> 
   <td colname="col2"> <p>El servicio de ID de visitante envió una solicitud y recibió una respuesta correcta del servidor. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> NULL</span> </p> </td> 
   <td colname="col2"> <p>El servicio de ID de visitante no envió una solicitud. </p> </td> 
  </tr> 
 </tbody> 
</table>

