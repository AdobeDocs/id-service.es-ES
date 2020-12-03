---
description: Casos de uso y soluciones de ejemplo para la administración del servicio de inclusión (Opt-in).
seo-description: Casos de uso y soluciones de ejemplo para la administración del servicio de inclusión (Opt-in).
seo-title: Casos de uso de Opt-in
title: Casos de uso de Opt-in
uuid: d75a44d5-b713-43d1-b5b6-95d1d0d213a7
translation-type: tm+mt
source-git-commit: 0c300aa92991c0dec2ccdeeb34f9d886dcac7671
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 16%

---


# Casos de uso de Opt-in {#opt-in-use-cases}

Casos de uso y soluciones de ejemplo para la administración del servicio de inclusión (Opt-in).

## Sugerencias y solución de problemas {#section-5c566366410f4a8f89eca0d3f556d99f}

* La inicialización de JS de visitante es sincrónica y se ejecuta durante la carga de página. Si está interactuando con un CMP o una persistencia de permisos con una latencia alta, puede que sea preferible utilizar las funciones asincrónicas descritas en Configuración [de](../../implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047)selección.
* La inclusión es una implementación por dominio. No gestionará implementaciones entre dominios.
* Para deshabilitar las llamadas de terceros para una biblioteca específica, deberá configurar esa preferencia en cada biblioteca por separado.

## Situaciones de inclusión  {#section-1178053c065c430bba26f82ef383a71c}

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
   <td colname="col1"> <p>Analytics está bien para recopilar en estado de preconsentimiento, pero todas las demás bibliotecas no se pueden cargar hasta que se reciba el consentimiento </p> </td> 
   <td colname="col2"> <p>Utilice la opción de inclusión para habilitar la categoría de Analytics en el estado de preconsentimiento </p> </td> 
   <td colname="col3"> <p>Analytics utiliza el identificador de Analytics en lugar de ECID en la colección de preconsentimiento. Una vez aprobado el ECID, se utilizará un nuevo identificador y el visitante recibirá un ECID que puede utilizarse para la activación y las integraciones. </p> <p>Se espera la fragmentación del visitante en el estado previo y posterior al consentimiento. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>La medición de origen está bien para recopilarla en estado previo al consentimiento. Se impidió el uso de todos los demás tipos de datos hasta que se recibiera el consentimiento. </p> </td> 
   <td colname="col2"> <p>Utilice la opción de inclusión para habilitar las bibliotecas de Analytics + ECID en estado de preconsentimiento. </p> <p>Añada la configuración ‘disablethirdpartycookies’ a la biblioteca ECID para bloquear las sincronizaciones de cookies de terceros + ID en estado previo al consentimiento </p> </td> 
   <td colname="col3"> <p>La llamada de Demdex de Adobe se activará para la recuperación de ECID, pero no habrá ninguna cookie de Demdex, ni otras cookies de terceros ni sincronizaciones de ID presentes. </p> <p>Mantiene un visitante constante en el estado previo o posterior al consentimiento para Analytics. La recopilación en estado previo al consentimiento estará vinculada a la recopilación de datos posterior al consentimiento. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>La medición de origen más la segmentación es aceptable en un estado previo al consentimiento. Se impidió el uso de todos los demás tipos de datos hasta que se recibiera el consentimiento. </p> </td> 
   <td colname="col2"> <p>Utilice la opción de inclusión para habilitar las bibliotecas de Analytics + ECID + Destinatario en estado de preconsentimiento. </p> <p>Agregue la configuración <span class="codeph">isablethirdpartycookies</span> a la biblioteca ECID para bloquear las cookies de terceros y las sincronizaciones de ID previamente al consentimiento. Eliminar indicador en estado posterior al consentimiento. </p> </td> 
   <td colname="col3"> <p>La llamada de Demdex de Adobe se activará para la recuperación de ECID, pero no habrá ninguna cookie de Demdex, ni otras cookies de terceros ni sincronizaciones de ID presentes. </p> <p>Mantiene un visitante constante en el estado previo y posterior al consentimiento para las soluciones de origen. La recopilación en estado previo al consentimiento estará vinculada a la recopilación de datos posterior al consentimiento. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>No se permite configurar cookies en un estado previo al consentimiento </p> </td> 
   <td colname="col2"> <p>Utilice la opción de inclusión para bloquear la carga de todas las bibliotecas hasta que se reciba el consentimiento </p> </td> 
   <td colname="col3"> <p>La implementación es la esperada y todas las bibliotecas, incluido ECID, se cargarán en la secuencia correcta en el estado posterior al consentimiento. </p> <p>Pérdida de datos para clientes que nunca dan su consentimiento para ser rastreados. </p> </td> 
  </tr> 
 </tbody> 
</table>

