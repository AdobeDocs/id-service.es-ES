---
description: Junto con el ID de visitante de Experience Cloud, se pueden asociar ID de cliente adicionales y un estado de autenticación a cada visitante.
keywords: Servicio de ID
seo-description: Junto con el ID de visitante de Experience Cloud, se pueden asociar ID de cliente adicionales y un estado de autenticación a cada visitante.
seo-title: ID de cliente y estados de autenticación
title: ID de cliente y estados de autenticación
uuid: 643df363-224a-463e-a332-be59926b47e7
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# ID de cliente y estados de autenticación {#customer-ids-and-authentication-states}

Junto con el ID de visitante de Experience Cloud, se pueden asociar ID de cliente adicionales y un estado de autenticación a cada visitante.

## Estados de autenticación {#section-68ad4065dfaa437d9070832d6e2bf85c}

El `setCustomerIDs` método acepta múltiples ID de cliente para el mismo visitante. Ayuda a identificar o dirigirse a un usuario individual entre distintos dispositivos. Por ejemplo, puede cargar estos ID como [atributos de cliente](https://marketing.adobe.com/resources/help/en_US/mcloud/?f=attributes.html) a [!DNL Experience Cloud] y acceder a estos datos en las distintas soluciones.

>[!IMPORTANT]
>
>Los atributos de clientes y la funcionalidad de los servicios principales requieren el uso de `setCustomerIDs` (sincronización de ID de clientes). La sincronización de los ID de cliente es un método de identificación opcional para [!DNL Analytics]. [!DNL Target] exige el uso de `Visitor.AuthState.AUTHENTICATED` para que funcionen los atributos de cliente. Consulte [Servicios principales - Cómo activar sus soluciones](https://marketing.adobe.com/resources/help/en_US/mcloud/?f=core_services) para ver ejemplos.

Beginning with Experience Cloud Identity Service v1.5+, `setCustomerIDs` includes the optional `AuthState` object. `AuthState` identifica a los visitantes en función de su estado de autenticación (por ejemplo, conectado, desconectado). Usted establece el estado de autenticación con un valor de estado que aparece en la tabla. El estado de autenticación se devuelve como un número entero.

<table id="table_8547671CC97145529981FBF6C302BEC5"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Estado de autenticación </th> 
   <th colname="col2" class="entry"> Número entero de estado </th> 
   <th colname="col3" class="entry"> Estado de usuario </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.UNKNOWN </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 0 </span> </p> </td> 
   <td colname="col3"> <p>Desconocido o nunca autenticado. </p> <p> El valor de desconocido se aplica de manera predeterminada cuando no se usa <span class="codeph">AuthState</span> con un ID de visitante o no se establece explícitamente en cada página o contexto de la aplicación. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 1 </span> </p> </td> 
   <td colname="col3"> <p>Autenticado para una instancia, página o aplicación particulares. </p> <p> <p>Atención: Para poder funcionar correctamente, los atributos de cliente para <span class="keyword">Target</span> deben tener este estado. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">2</span> </p> </td> 
   <td colname="col3"> <p>Desconectado. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Casos de uso para estados de autenticación {#section-fe9560cc490943b29dac2c4fb6efd72c}

Puede asignar estados de autenticación a sus usuarios, en función de las acciones que estén realizando en sus propiedades web y de si están autenticados. Puede ver algunos ejemplos en la tabla siguiente:

<table id="table_3769E79304014C4F87094B87A8ACE4E0"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Estado de autenticación </th> 
   <th colname="col2" class="entry"> Caso de uso </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.UNKNOWN </span> </p> </td> 
   <td colname="col2"> <p>Este estado podría utilizarse para situaciones tales como: </p> <p> 
     <ul id="ul_086C7446D258443DA7AF5BB96A6AAEC7"> 
      <li id="li_7845BBD62D7B4362AD3FE33DEDA8FBA1">Leer un correo electrónico (esta acción probablemente signifique que el lector es el destinatario previsto, aunque también puede tratarse de un mensaje reenviado). </li> 
      <li id="li_FAB7ACFC69624631BD01FC0ED84B23C5">Hacer clic en un vínculo en un mensaje de correo electrónico y llegar a una página de aterrizaje. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p>El usuario está autenticado con una sesión activa en su sitio web o aplicación. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p>El usuario estaba autenticado pero ha cerrado sesión activamente. El usuario quería desconectarse del estado autenticado. El usuario ya no quiere que se le trate como autenticado. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Establecimiento de ID de cliente y estados autenticados {#section-ec4b367d16ad4ac1a1baca9b01f4ee98}

Los ID de cliente pueden incluir combinaciones de ID y estados autenticados, como se muestra en los ejemplos siguientes.

>[!IMPORTANT]
>
>* En los ID se distingue entre mayúsculas y minúsculas.
>* Emplee únicamente valores descodificados para sus ID.
>* Los ID de cliente y los estados de autenticación no se almacenan en la cookie de ID de visitante. Deben establecerse para cada página o contexto de aplicación.
>* En los ID de cliente no se debe incluir información de identificación personal. Si actualmente utiliza información de este tipo para identificar a algún visitante (como una dirección de correo electrónico), le recomendamos que almacene una versión con hash o cifrada de la información.
>



```js
// Single ID with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
/* 
Multiple IDs with only the first ID explicitly assigned an authentication state. 
The second ID is not explicitly assigned an authentication state and is implicitly 
assigned Visitor.AuthState.Unknown by default. 
*/ 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "puuid":"550e8400-e29b-41d4-a716-446655440000" 
}); 
 
// Multiple IDs with identical authentication states 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "puuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
// Multiple IDs with different authentication states 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "puuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":Visitor.AuthState.LOGGED_OUT 
    } 
}); 
```

## Devolución de ID de cliente y estados autenticados {#section-71a610546188478fa9a3185a01d6e83b}

Utilice `getCustomerIDs` para devolver ID de cliente y estados autenticados relacionados. Este método devuelve un estado autenticado de visitante como un número entero.

**Sintaxis**

`getCustomerIDs` devuelve datos con la sintaxis siguiente.

```js
{ 
    [customerIDType1]:{ 
        "id":[customerID1], 
        "authState":[authState1] 
    }, 
    [customerIDType2]:{ 
        "id":[customerID2], 
        "authState":[authState2] 
    } 
    ... 
}
```

**Ejemplos**

Los datos de ID de cliente y de estado de autenticación devueltos deben tener un aspecto similar al de los ejemplos siguientes.

```js
Object customerIDs = visitor.getCustomerIDs(); 
  
// No setCustomerIDs call on this instance 
{} 
  
// setCustomerIDs call on this instance with {"userid":{"id":"67312378756723456"}} 
{ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":0 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"id":"67312378756723456","authState":Visitor.AuthState.AUTHENTICATED}} 
{ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":1 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"authState":Visitor.AuthState.LOGGED_OUT}} 
{ 
    "userid":{ 
        "authState":2 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"authState":Visitor.AuthState.LOGGED_OUT},"puuid":{"id":"550e8400-e29b-41d4-a716-446655440000"}} 
{ 
    "userid":{ 
        "authState":2 
    }, 
    "puuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":0 
    } 
 }
```

## Compatibilidad con SDK {#section-861c6b3b1ba645dda133dccb22ec7bb0}

El servicio de ID de [!DNL Experience Cloud] admite ID de clientes y estados de autenticación en nuestro código SDK para Android y para iOS. Consulte las siguientes bibliotecas de código:

* [Métodos SDK para Android](https://marketing.adobe.com/resources/help/en_US/mobile/android/?f=c_marketing_cloud.html)
* [Métodos SDK para iOS](https://marketing.adobe.com/resources/help/en_US/mobile/ios/?f=marketing_cloud.html)

## Aviso para clientes de Analytics y Audience Manager {#section-3a8e9d51e71c4c6e865184b81ed9d99b}

Si va a pasar ID declarados a [!DNL Audience Manager], el objeto `userid` deberá coincidir con el código de integración asociado a la fuente de datos. For more information, see the [!DNL Visitor ID Service] section in the [Configure Merge Rules Code](https://marketing.adobe.com/resources/help/en_US/aam/?f=merge-rules-configure-code.html) documentation.
