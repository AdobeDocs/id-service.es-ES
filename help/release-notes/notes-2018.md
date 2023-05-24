---
description: Versiones de funcionalidades, actualizaciones o cambios en el servicio de Experience Cloud ID para 2018.
keywords: Servicio de ID
title: Notas de la versión de 2018
exl-id: ad3cccf1-2753-4ac9-a68c-15b2d62bbc1a
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 100%

---

# Notas de la versión 2018 {#release-notes}

Versiones de funcionalidades, actualizaciones o cambios en el servicio de Experience Cloud ID para 2018.

## Versión 3.3 {#section-3202c8d5457a45a5b5f4b4c838d44de3}

<table id="table_201417BD540E4EE69911AABE9BF77509"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Descripción del elemento </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Mayor seguridad para las cookies AMCV </p> </td> 
   <td colname="col2"> <p>Durante un análisis de seguridad interna, se descubrió que, al usar la biblioteca de DTM, las cookies que se utilizaban para la administración de sesiones no especificaban los atributos adecuados. Esto podría hacer que la información de las cookies se compartiera de forma involuntaria. Para solucionarlo, hemos introducido una configuración que permite al cliente definir la cookie AMCV como segura. Consulte <a href="/help/library/function-vars/securecookie.md" format="https" scope="external">secureCookie</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Versión 3.2 {#section-ae2fee1c152e405faa4eb395f960e2f6}

<table id="table_6546F5C74E4742E4B5E9793BCEAB66FA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Descripción del elemento </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Mayor seguridad para las cookies AMCV </p> </td> 
   <td colname="col2"> <p>Durante un análisis de seguridad interna, se descubrió que, al usar la biblioteca de DTM, las cookies que se utilizaban para la administración de sesiones no especificaban los atributos adecuados. Esto podría hacer que la información de las cookies se compartiera de forma involuntaria. Para solucionarlo, hemos introducido una configuración que permite al cliente definir la cookie AMCV como segura. Consulte secureCookie. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>El código de integración y el ID deben ser números o cadenas que no estén vacías </p> </td> 
   <td colname="col2"> <p>Se ha corregido un problema relativo a la validación de “setCustomerIDs” en los casos en los que los datos contienen un valor “code” o “id” de integración que no es un número ni una cadena que no esté vacía. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> ECID JS está disponible en el repositorio Git público </td> 
   <td colname="col2"> ECID JS ya está disponible en el repositorio Git público para todos los clientes Experience Cloud en https://github.com/Adobe-Marketing-Cloud/id-service/releases. </td> 
  </tr> 
 </tbody> 
</table>

## Versión 3.1.2 {#section-3cba186f74fe4f2186a9ca2e5e0a2514}

<table id="table_9FA4E20C996746A2A4219C9A0F759AD1"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Descripción del elemento </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Repunte poco realista en la cantidad de visitantes únicos </p> </td> 
   <td colname="col2"> <p>Con el lanzamiento del servicio de identidad de Experience Cloud 3.1.0 se encontró un problema que creaba un repunte poco realista en la cantidad de visitantes únicos tras la implementación de esta versión. Este comportamiento solo se muestra con la última versión de ECID, la 3.1.0, y si un usuario ha seleccionado la opción Permitir solo desde el sitio web actual en la configuración de privacidad de un explorador Safari. La versión 3.1.2 corrige este problema. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Versión 3.1.0 {#section-a20c8278bf9643018965330415091e53}

>[!NOTE]
>
>Se recomienda que actualice lo antes posible de la versión 3.1.0 a la más reciente. Consulte la descripción de la versión 3.1.2. El paquete más reciente está disponible en Adobe Experience Platform Launch, DTM y AppMeasurement

<table id="table_512039AFC4D34038B8F116B71EEEE7F6"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Descripción del elemento </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Cookie establecida en un dominio incorrecto </p> </td> 
   <td colname="col2"> <p>Se ha corregido un error por el que la cookie temporal de visitante establecía una cookie en el dominio de cookie predeterminado en lugar de establecerla en el dominio que se proporciona en la configuración (initConfig). </p> </td> 
  </tr> 
 </tbody> 
</table>

## Versión 3.0 {#section-5fcaef66e8b343238abeb10048dc5747}

<table id="table_7E9224D6CC924A2DB5119171C9DC5443"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Descripción del elemento </th> 
   <th colname="col2" class="entry"> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Separación de procesos cuando hay varias solicitudes de sincronización de ID </p> </td> 
   <td colname="col2"> <p><b>Iframe</b> </p> <p>A veces, a los clientes que realizan varias sincronizaciones de ID se les bloquea la IU debido a que ocurren continuas computaciones de CPU. Estamos introduciendo el rendimiento de subprocesos para separar las solicitudes de sincronización de identificación con periodos de 100 ms entre cada una. </p> <p>Este cambio mejorará el rendimiento de los clientes que utilizan Visitor 2.3.0 o posterior y DIL 6.10 o posterior. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Se ha añadido la capacidad de desactivar las llamadas de terceros. </td> 
   <td colname="col2"> <p><b>JavaScript: 3.0.0</b> </p> <p>Adobe ha cambiado el nombre de las siguientes configuraciones para permitir la desactivación de las llamadas de sincronización de terceros. </p> <p>idSyncDisableSyncs a disableIdSyncs </p> <p>idSyncDisable3rdPartySyncing a disableThirdPartyCookies </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Compatibilidad con Internet Explorer </p> </td> 
   <td colname="col2"> <p>El servicio de ID ya no es compatible con Internet Explorer 6, 7, 8 y 9. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Actualización de la documentación de getInstance </p> </td> 
   <td colname="col2"> <p>Se ha agregado a la función Visitante la advertencia de que no debe crearse una instancia de esta con var visitor = new Visitor. </p> </td> 
  </tr> 
 </tbody> 
</table>
