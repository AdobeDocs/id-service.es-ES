---
description: Llame a estas funciones del servicio de identidad para determinar el estado de tiempo de espera de una solicitud de ID del servicio de identidad de Experience Cloud, Analytics o de Audience Manager. Disponible en VisitorAPI.js versión 1.7.0 o posteriores.
keywords: Servicio de ID
seo-description: Llame a estas funciones del servicio de ID para determinar el estado de tiempo de espera de una solicitud de ID del servicio de Experience Cloud ID, Analytics o de Audience Manager. Disponible en VisitorAPI.js versión 1.7.0 o posteriores.
seo-title: Métodos callTimeOut
title: Métodos callTimeOut
uuid: e5047498-11db-4945-b356-c92b7d447573
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# Métodos callTimeOut{#calltimeout-methods}

Llame a estas funciones del servicio de ID para determinar el estado de tiempo de espera de una solicitud de ID del servicio de Experience Cloud ID, Analytics o de Audience Manager. Disponible en VisitorAPI.js versión 1.7.0 o posteriores.

## Funciones de tiempo de espera {#section-e08228ef5f9b45c9a84139bbb763164a}

<table id="table_B3ACE584B3224D838070D32A8462EF28"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Solución o servicio </th> 
   <th colname="col2" class="entry"> Sintaxis de función </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Servicio de Experience Cloud ID </p> </td> 
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

## Respuestas de las funciones {#section-ff73aaca58b74e10a0953c49a3387160}

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
   <td colname="col2"> <p>El servicio de ID envió una solicitud y esta alcanzó su tiempo de espera máximo. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> FALSE</span> </p> </td> 
   <td colname="col2"> <p>El servicio de ID envió una solicitud y recibió una respuesta correcta del servidor. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> NULL</span> </p> </td> 
   <td colname="col2"> <p>El servicio de ID no envió una solicitud. </p> </td> 
  </tr> 
 </tbody> 
</table>

