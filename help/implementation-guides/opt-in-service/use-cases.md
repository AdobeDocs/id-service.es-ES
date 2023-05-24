---
description: Casos de uso y soluciones de ejemplo para la administración del servicio de inclusión (Opt-in).
title: Casos de uso de Opt-in
exl-id: 4c57685f-40b7-4af4-8527-3c2795586f0f
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 100%

---

# Casos de uso de Opt-in {#opt-in-use-cases}

Casos de uso y soluciones de ejemplo para la administración del servicio de inclusión (Opt-in).

## Sugerencias y solución de problemas {#section-5c566366410f4a8f89eca0d3f556d99f}

* La inicialización de Visitor JS es sincrónica y se ejecuta durante la carga de la página. Si está interactuando con una CMP o con una persistencia de permisos que tenga una latencia alta, puede que sea preferible utilizar las funciones asincrónicas descritas en [Configuración de inclusión](../../implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047).
* La inclusión es una implementación por dominio. No gestiona implementaciones entre dominios.
* Para deshabilitar las llamadas de terceros para una biblioteca específica, deberá configurar esa preferencia en cada biblioteca por separado.

## Situaciones de inclusión {#section-1178053c065c430bba26f82ef383a71c}

Estos casos de uso son ejemplos del uso del servicio de inclusión (Opt-in).

<table id="table_83C85343611344D8A8315157C1B4240F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Requisito </th> 
   <th colname="col2" class="entry"> Soluciones </th> 
   <th colname="col3" class="entry"> Impacto </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Analytics puede recopilar en estado previo al consentimiento, pero el resto de las bibliotecas no se pueden cargar hasta que se reciba el consentimiento </p> </td> 
   <td colname="col2"> <p>Utilice la inclusión para habilitar la categoría Analytics previamente al consentimiento </p> </td> 
   <td colname="col3"> <p>Analytics utiliza el identificador de Analytics en lugar de ECID en la colección previa al consentimiento. Una vez aprobado el ECID, se utilizará un nuevo identificador y el visitante recibirá un ECID que se puede utilizar para la activación y las integraciones. </p> <p>Se espera la fragmentación de visitantes en estado previo/posterior al consentimiento. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>La medición de origen está bien para recopilarla previamente al consentimiento. Se ha impedido el uso de todos los demás tipos de datos hasta que se reciba el consentimiento. </p> </td> 
   <td colname="col2"> <p>Utilice la inclusión para habilitar bibliotecas de Analytics + ECID previamente al consentimiento. </p> <p>Añada la configuración disablethirdpartycookies a la biblioteca ECID para bloquear las cookies de terceros y las sincronizaciones de ID previamente al consentimiento </p> </td> 
   <td colname="col3"> <p>La llamada de Demdex de Adobe se activará para la recuperación de ECID, pero no habrá presente ninguna cookie de Demdex, otras cookies de terceros ni sincronizaciones de ID. </p> <p>Mantiene al visitante coherente en estado previo/posterior al consentimiento para Analytics. La colección en estado previo al consentimiento estará vinculada a la recopilación de datos posterior al consentimiento. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>La medición de origen más el direccionamiento es aceptable en un estado previo al consentimiento. Se ha impedido el uso de todos los demás tipos de datos hasta que se reciba el consentimiento. </p> </td> 
   <td colname="col2"> <p>Utilice la inclusión para habilitar bibliotecas de Analytics + ECID + Target previamente al consentimiento. </p> <p>Agregue la configuración <span class="codeph">isablethirdpartycookies</span> a la biblioteca ECID para bloquear las cookies de terceros y las sincronizaciones de ID previamente al consentimiento. Quite el indicador en estado posterior al consentimiento. </p> </td> 
   <td colname="col3"> <p>La llamada de Demdex de Adobe se activará para la recuperación de ECID, pero no habrá presente ninguna cookie de Demdex, otras cookies de terceros ni sincronizaciones de ID. </p> <p>Mantiene al visitante consistente en estado previo/posterior al consentimiento para soluciones de origen. La colección en estado previo al consentimiento estará vinculada a la recopilación de datos posterior al consentimiento. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>No se permite establecer cookies previamente al consentimiento </p> </td> 
   <td colname="col2"> <p>Utilice la inclusión para impedir que todas las bibliotecas se carguen hasta que se reciba el consentimiento </p> </td> 
   <td colname="col3"> <p>La implementación es la esperada y todas las bibliotecas, incluido ECID, se cargarán en la secuencia correcta en el estado posterior al consentimiento. </p> <p>Pérdida de datos para clientes que nunca dan su consentimiento para que se rastree. </p> </td> 
  </tr> 
 </tbody> 
</table>
