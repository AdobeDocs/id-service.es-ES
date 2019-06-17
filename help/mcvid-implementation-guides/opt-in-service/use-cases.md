---
description: Ejemplos de uso de muestra y soluciones para administrar el servicio de selección.
seo-description: Ejemplos de uso de muestra y soluciones para administrar el servicio de selección.
seo-title: Casos de uso de Opt-in
title: Casos de uso de Opt-in
uuid: d 75 a 44 d 5-b 713-43 d 1-b 5 b 6-95 d 1 d 0 d 213 a 7
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Casos de uso de Opt-in {#opt-in-use-cases}

Ejemplos de uso de muestra y soluciones para administrar el servicio de selección.

## Sugerencias y solución de problemas {#section-5c566366410f4a8f89eca0d3f556d99f}

* La inicialización de Visitor JS es sincrónica y se ejecuta durante la carga de la página. Si se está relacionando con una CMP o con la persistencia de permisos con una gran latencia, podría ser preferible utilizar las funciones asíncronas descritas en [Configuración de Opt-in](../../mcvid-implementation-guides/opt-in-service/getting-started.md#section-cf9ab638780141c9b62dc57cf00b7047).
* Opt-in es una implementación por dominio. No gestiona las implementaciones entre dominios.
* Si desea deshabilitar las llamadas de terceros para una biblioteca específica, debe configurar esa preferencia separadamente en cada biblioteca.

## Situaciones de inclusión {#section-1178053c065c430bba26f82ef383a71c}

Estos casos de uso son ideas de ejemplo para utilizar el servicio de selección.

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
   <td colname="col1"> <p>Analytics puede recopilar datos previamente al consentimiento, pero las demás bibliotecas no se pueden cargar hasta haber recibido consentimiento </p> </td> 
   <td colname="col2"> <p>Utilice Opt-in para habilitar la categoría Analytics previamente al consentimiento </p> </td> 
   <td colname="col3"> <p>Analytics utiliza el identificador Analytics en vez de ECID en la recopilación previa al consentimiento. Una vez aprobado el ECID, se utilizará un nuevo identificador y el visitante recibirá un ECID que puede utilizarse para activación y para integraciones. </p> <p>Cabe esperar la fragmentación de los visitantes en los estados anterior y posterior al consentimiento. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Se pueden recopilar mediciones de origen previamente al consentimiento. Se impedirá cualquier otro uso de los datos hasta que se cuente con consentimiento. </p> </td> 
   <td colname="col2"> <p>Utilice Opt-in para habilitar bibliotecas de Analytics + ECID previamente al consentimiento. </p> <p>Agregue la configuración “disablethirdpartycookies” a la biblioteca ECID para bloquear las cookies de terceros y las sincronizaciones de ID previamente al consentimiento </p> </td> 
   <td colname="col3"> <p>La llamada a Adobe Demdex se activará para la recuperación de ECID, pero no habrá presente ninguna cookie demdex, ninguna otra cookie de terceros ni ninguna sincronización de ID. </p> <p>Mantiene al visitante consecuente en estado previo o anterior al consentimiento para Analytics. La recopilación previa al consentimiento quedará vinculada a la recopilación de datos posterior al consentimiento. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>La medición de origen y la segmentación son aceptables previamente al consentimiento. Se impedirá cualquier otro uso de los datos hasta que se cuente con consentimiento. </p> </td> 
   <td colname="col2"> <p>Utilice Opt-in para habilitar bibliotecas de Analytics + ECID + Target previamente al consentimiento. </p> <p>Agregue la configuración <span class="codeph">isablethirdpartycookies</span> a la biblioteca ECID para bloquear las cookies de terceros y las sincronizaciones de ID previamente al consentimiento. Elimine el indicador en el estado posterior al consentimiento. </p> </td> 
   <td colname="col3"> <p>La llamada a Adobe Demdex se activará para la recuperación de ECID, pero no habrá presente ninguna cookie demdex, ninguna otra cookie de terceros ni ninguna sincronización de ID. </p> <p>Mantiene al visitante consecuente en estado previo o anterior al consentimiento para soluciones de origen. La recopilación previa al consentimiento quedará vinculada a la recopilación de datos posterior al consentimiento. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>No se permite el establecimiento de cookies previamente al consentimiento </p> </td> 
   <td colname="col2"> <p>Utilice Opt-in para impedir la carga de todas las bibliotecas hasta que se haya recibido el consentimiento </p> </td> 
   <td colname="col3"> <p>La implementación es la esperada y todas las bibliotecas, incluida ECID, se cargarán en la secuencia correcta en el estado posterior al consentimiento. </p> <p>Pérdida de datos para los clientes que no dan el consentimiento para su seguimiento. </p> </td> 
  </tr> 
 </tbody> 
</table>

