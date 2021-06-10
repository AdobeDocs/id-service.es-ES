---
description: Una configuración booleana opcional que determina si el servicio de ID envía datos (o no) a Device Co-Op de Adobe Experience Cloud.
keywords: Servicio de ID
title: isCoopSafe
exl-id: 827f7819-9f95-4e8d-90c3-dcf86b67715b
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# isCoopSafe{#iscoopsafe}

Una configuración booleana opcional que determina si el servicio de ID envía datos (o no) a Device Co-Op de Adobe Experience Cloud.

Contenido:

<ul class="simplelist"> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-4883eda6beb8437182bcc82bb58fae41" format="dita" scope="local"> Requisitos </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-d18af2b903f248e18ae8108aaf0a8ebb" format="dita" scope="local"> Casos de uso </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-952f56724a2b4d349340e26fbaf33ddd" format="dita" scope="local"> Ejemplo de sintaxis y código </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-fcd441933506493faefaa6b51f194a17" format="dita" scope="local"> Parámetros POST de llamada de evento </a> </li> 
 <li> <a href="../../library/function-vars/coopsafe.md#section-9281c39c8b6249d7864100b5cbca7dc6" format="dita" scope="local"> API posteriores a la creación de instancias </a> </li> 
</ul>

## Requisitos {#section-4883eda6beb8437182bcc82bb58fae41}

Para utilizar `isCoopSafe`, debe:

* Utilizar el código de servicio de ID versión 2.4 o posterior.
* Participe en [Experience Cloud Device Co-op](https://docs.adobe.com/content/help/es-ES/device-co-op/using/about/overview.html). Los potenciales miembros de la cooperación también deben revisar esta documentación para determinar si `isCoopSafe` soluciona los posibles problemas sobre cómo se utilizan los datos para crear el gráfico de dispositivos.

* Trabaje con su consultor de [!DNL Adobe] para establecer un indicador de lista de elementos permitidos o de lista de elementos bloqueados en su cuenta de Device Co-Op. No existe una ruta de autoservicio que permita habilitar estos indicadores.

## Casos de uso {#section-d18af2b903f248e18ae8108aaf0a8ebb}

`isCoopSafe` ayuda a resolver dos casos de uso relacionados con la recopilación de datos que efectúan los miembros actuales o potenciales de Device Co-Op. Estos casos de uso están relacionados con la forma en la que se pasan los datos de visitantes del sitio a Device Co-Op para ayudar a crear el gráfico de dispositivos. En la tabla siguiente se describe cómo `isCoopSafe` funciona con estos casos de uso para bloquear o enviar datos al gráfico de dispositivos.

<table id="table_A24C63D2A21F47EDBAC8FA5E7BE888D8"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Caso de uso </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Visitantes autenticados</b> </p> </td> 
   <td colname="col2"> <p>Agregue <span class="codeph">isCoopSafe</span> a su código de servicio de ID para controlar cómo Device Co-Op utiliza los datos para los visitantes autenticados que han aceptado o no los acuerdos de condiciones de uso para crear el gráfico de dispositivos. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>DIL en sitios de terceros</b> </p> </td> 
   <td colname="col2"> <p>Agregue <span class="codeph">isCoopSafe</span> a su código de servicio de ID para usarlo en sitios de terceros en los que: </p> <p> 
     <ul id="ul_C27BB26510314834A2A7CD99D46DA4AC"> 
      <li id="li_4E6AE574F18646F09C0CF4553EEA1A9E">No se puede garantizar que los visitantes autenticados hayan aceptado o no acuerdos de términos de uso. </li> 
      <li id="li_26D0561BF32B4278B0A6B5082C17FED8">Es necesario controlar cómo Device Co-op utiliza esos datos para crear el gráfico del dispositivo. </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Ejemplo de sintaxis y código {#section-952f56724a2b4d349340e26fbaf33ddd}

**Sintaxis:** `isCoopSafe: true | false`

Las opciones booleanas determinan cómo Device Co-Op utiliza o no los datos de cliente.

* `isCoopSafe: true`: los datos de visitante recopilados por un SDK móvil o sitio web se *pueden* utilizar para ayudar a crear el gráfico de dispositivos.

* `isCoopSafe: false`: los datos de visitante recopilados por un SDK móvil o sitio web *no se pueden* utilizar para ayudar a crear el gráfico de dispositivos.

**Ejemplo de código**

Establezca esta opción cuando el código del servicio de ID cree una instancia:

```js
var visitor = Visitor.getInstance("Insert Experience Cloud organization ID here",{ 
     ... 
     isCoopSafe: true 
});
```

## Parámetros POST de llamada de evento  {#section-fcd441933506493faefaa6b51f194a17}

En función del indicador que establezca (`true` o `false`), el servicio de ID traduce `isCoopSafe` a estos parámetros POST y los envía a [!DNL Adobe] en una llamada de evento:

* `d_coop_safe=1`
* `d_coop_unsafe=1`

Los parámetros POST indican a [!DNL Experience Cloud] Device Co-Op de si puede incluir o no datos en el gráfico de dispositivos. En la siguiente tabla se define la relación entre los indicadores booleanos `isCoopSafe` y los parámetros POST que se han transferido en una llamada de evento. Si no utiliza `isCoopSafe`, no se transferirá ninguno de estos elementos en una llamada de evento.

<table id="table_0A544534CA904F4D9836A34B8C1EACBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Estado de configuración </th> 
   <th colname="col2" class="entry"> Parámetro POST </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe: true </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> d_coop_safe=1 </span> </p> <p>Device Co-Op puede utilizar los datos de visitante para ayudar a crear el gráfico de dispositivos. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> isCoopSafe: false </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> d_coop_unsafe=1 </span> </p> <p>Device Co-Op no puede utilizar los datos de visitante para ayudar a crear el gráfico de dispositivos. </p> </td> 
  </tr> 
 </tbody> 
</table>

## API posteriores a la creación de instancias  {#section-9281c39c8b6249d7864100b5cbca7dc6}

Estas API permiten sobrescribir el estado de `isCoopSafe`. Esto es necesario porque le permiten cambiar el estado posterior a la creación de la instancia o al inicio de sesión de un visitante en un sitio o en una aplicación de una sola página en la que la página no se actualiza. Por ejemplo, debe llamar a estas API si un usuario se autentica en su sitio o aplicación y luego acepta una política de términos de uso que permita a Device Co-op utilizar sus datos.

<table id="table_BAA96B1F82BE48C3A61A1AF1367BA45C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> API </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> visitor.setAsCoopSafe(); </span> </p> </td> 
   <td colname="col2"> <p>Establece el parámetro POST <span class="codeph">d_coop_safe=1</span> en todas las llamadas de evento posteriores. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> visitor.setAsCoopUnsafe(); </span> </p> </td> 
   <td colname="col2"> <p>Establece el parámetro POST <span class="codeph">d_coop_unsafe=1</span> en todas las llamadas de evento posteriores. </p> </td> 
  </tr> 
 </tbody> 
</table>

<!--
Wiki page https://wiki.corp.adobe.com/x/RCfFTg
-->

>[!MORELIKETHIS]
>
>* [DIL isCoopSafe](https://docs.adobe.com/content/help/es-ES/audience-manager/user-guide/dil-api/class-level-dil-methods/dil-coopsafe.html)

