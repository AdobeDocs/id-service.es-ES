---
description: Llame a estas funciones del servicio de ID para determinar el estado de tiempo de espera de una solicitud de ID del servicio de Experience Cloud ID, Analytics o de Audience Manager. Disponible en VisitorAPI.js versión 1.7.0 o posteriores.
keywords: Servicio de ID
title: Métodos callTimeOut
exl-id: ff3a2c5e-a0a8-4257-b538-0e4ce454b4e8
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 100%

---

# Métodos callTimeOut {#calltimeout-methods}

Llame a estas funciones del servicio de ID para determinar el estado de tiempo de espera de una solicitud de ID del servicio de Experience Cloud ID, Analytics o de Audience Manager. Disponible en VisitorAPI.js versión 1.7.0 o posteriores.

## Funciones de tiempo de espera  {#section-e08228ef5f9b45c9a84139bbb763164a}

<table id="table_B3ACE584B3224D838070D32A8462EF28"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Solución o servicio </th> 
   <th colname="col2" class="entry"> Sintaxis de funciones </th> 
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
