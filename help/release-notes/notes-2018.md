---
description: Versiones de funcionalidades, actualizaciones o cambios en el servicio de identidad de Experience Cloud para 2018.
keywords: Servicio de ID
seo-description: Versiones de funcionalidades, actualizaciones o cambios en el servicio de Experience Cloud ID para 2018.
seo-title: Notas de la versión 2018
title: Notas de la versión 2018
uuid: 771b5b11-a8e3-464c-b65e-b15135584ace
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

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
   <td colname="col1"> <p>Se ha mejorado la seguridad de las cookies AMCV </p> </td> 
   <td colname="col2"> <p>Durante un análisis de seguridad interna se descubrió que, al utilizar la biblioteca DTM, las cookies empleadas para la gestión de la sesión no especificaban atributos apropiados. Como resultado, podía compartirse de forma inadvertida información de las cookies. Para solucionar este problema hemos introducido una configuración que permite al cliente establecer la cookie AMCV como segura. Consulte <a href="/help/library/function-vars/securecookie.md" format="https" scope="external">secureCookie</a>. </p> </td> 
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
   <td colname="col1"> <p>Se ha mejorado la seguridad de las cookies AMCV </p> </td> 
   <td colname="col2"> <p>Durante un análisis de seguridad interna se descubrió que, al utilizar la biblioteca DTM, las cookies empleadas para la gestión de la sesión no especificaban atributos apropiados. Como resultado, podía compartirse de forma inadvertida información de las cookies. Para solucionar este problema hemos introducido una configuración que permite al cliente establecer la cookie AMCV como segura. Consulte secureCookie. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>El código de integración y el id deben ser números o cadenas no vacías </p> </td> 
   <td colname="col2"> <p>Se ha corregido un problema relativo a la validación de “setCustomerIDs” en los casos en los que los datos contienen un valor “code” o “id” de integración que no es un número ni una cadena que no esté vacía. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> ECID JS está disponible en el repositorio Git público </td> 
   <td colname="col2"> ECID JS ahora está disponible en el repositorio Git público para todos los clientes de Experience Cloud: https://github.com/Adobe-Marketing-Cloud/id-service/releases. </td> 
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
   <td colname="col1"> <p>Repunte poco realista en el recuento de visitantes únicos </p> </td> 
   <td colname="col2"> <p>Con el lanzamiento del servicio de identidad de Experience Cloud 3.1.0 se encontró un problema que creaba un repunte poco realista en el recuento de visitantes únicos tras la implementación de esta versión. Este comportamiento solo se produce con la última versión de ECID, v3.1.0, y si el usuario selecciona la opción “Permitir solo del sitio web actual” en los ajustes de privacidad del navegador Safari. La versión 3.1.2 corrige este problema. </p> </td> 
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
   <td colname="col2"> <p>Se ha corregido un error por el que la cookie de visitante temporal establecía una cookie en el dominio de cookie “predeterminado” en vez de hacerlo en el dominio indicado en la configuración (initConfig). </p> </td> 
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
   <td colname="col2"> <p><b>Iframe</b> </p> <p>A veces, a los clientes que realizan varias sincronizaciones de ID se les bloquea la IU debido a que ocurren continuas computaciones de CPU. Presentamos la separación de procesos para dividir las solicitudes de sincronización de ID en 100 ms cada una. </p> <p>Con este cambio, mejorará el rendimiento de los clientes que utilizan Visitor 2.3.0 o superior y DIL 6.10 o superior. </p> </td> 
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

