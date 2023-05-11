---
description: Junto con el ID de visitante de Experience Cloud, se pueden asociar ID de cliente adicionales y un estado de autenticación a cada visitante.
keywords: Servicio de ID
title: ID de cliente y estados de autenticación
exl-id: 0215225c-20f5-4e44-a368-b2df683aca9d
source-git-commit: 159b37e360b586bbada13e34793009e3067de668
workflow-type: ht
source-wordcount: '629'
ht-degree: 100%

---

# ID de cliente y estados de autenticación {#customer-ids-and-authentication-states}

Junto con el ID de visitante de Experience Cloud, se pueden asociar ID de cliente adicionales y un estado de autenticación a cada visitante.

## Estados de autenticación {#section-68ad4065dfaa437d9070832d6e2bf85c}

El `setCustomerIDs` método acepta múltiples ID de cliente para el mismo visitante. Ayuda a identificar o dirigirse a un usuario individual entre distintos dispositivos. Por ejemplo, puede cargar estos ID como [atributos de cliente](https://experienceleague.adobe.com/docs/core-services/interface/customer-attributes/attributes.html?lang=es) a [!DNL Experience Cloud] y acceder a estos datos en las distintas soluciones.

>[!IMPORTANT]
>
>Los atributos de clientes y la funcionalidad de los servicios principales requieren el uso de `setCustomerIDs` (sincronización de ID de clientes). La sincronización de los ID de cliente es un método de identificación opcional para [!DNL Analytics]. [!DNL Target] exige el uso de `Visitor.AuthState.AUTHENTICATED` para que funcionen los atributos de cliente. Consulte [Servicios principales - Cómo activar sus soluciones](https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html?lang=es) para ver ejemplos.

A partir del servicio de identidad de Experience Cloud de la versión 1.5 (o posterior), `setCustomerIDs` incluye el objeto opcional `AuthState`. `AuthState` identifica a los visitantes en función de su estado de autenticación (por ejemplo, conectado, desconectado). El estado de autenticación se establece con un valor de estado indicado en la tabla. El estado de autenticación se arroja como un número entero.

<table id="table_8547671CC97145529981FBF6C302BEC5"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Estado de autenticación </th> 
   <th colname="col2" class="entry"> Número entero de estado </th> 
   <th colname="col3" class="entry"> Estado del usuario </th> 
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
   <td colname="col2"> <p> <span class="codeph"> 2 </span> </p> </td> 
   <td colname="col3"> <p>Desconectado. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Casos de uso para estados de autenticación {#section-fe9560cc490943b29dac2c4fb6efd72c}

Puede asignar estados de autenticación a los usuarios, según las acciones que estén realizando en las propiedades web y si están autenticados. Consulte algunos ejemplos en la tabla siguiente:

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
   <td colname="col2"> <p>Este estado se puede usar para escenarios como: </p> <p> 
     <ul id="ul_086C7446D258443DA7AF5BB96A6AAEC7"> 
      <li id="li_7845BBD62D7B4362AD3FE33DEDA8FBA1">Leer un correo electrónico (esta acción probablemente significa que el lector es el destinatario deseado, pero también se podría haber reenviado el correo electrónico). </li> 
      <li id="li_FAB7ACFC69624631BD01FC0ED84B23C5">Navegando de un correo electrónico a una página de aterrizaje haciendo clic. </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p>El usuario está autenticado con una sesión activa en su sitio web o aplicación. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p>Se autenticó al usuario, pero se cerró la sesión de forma activa. El usuario quería desconectarse del estado autenticado. El usuario ya no quiere que se le considere autenticado. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Establecimiento de ID de cliente y estados autenticados {#section-ec4b367d16ad4ac1a1baca9b01f4ee98}

Los ID de cliente pueden incluir combinaciones de ID y estados autenticados, como se muestra en los ejemplos siguientes.

>[!IMPORTANT]
>
>* En los ID se distingue entre mayúsculas y minúsculas.
>* Emplee únicamente valores descodificados para sus ID.
>* Los ID de cliente y los estados de autenticación no se almacenan en la cookie de ID del visitante. Deben configurarse para cada página o contexto de aplicación.
>* No debe incluir información de identificación personal (PII) en los ID de cliente. Si actualmente utiliza información de este tipo para identificar a algún visitante (como una dirección de correo electrónico), le recomendamos que almacene una versión con hash o cifrada de la información. La biblioteca ECID proporciona compatibilidad con identificadores de usuario hash. Consulte [Soporte hash SHA 256 para setCustomerIDs](/help/reference/hashing-support.md).


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
    "dpuuid":"550e8400-e29b-41d4-a716-446655440000" 
}); 
 
// Multiple IDs with identical authentication states 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":{ 
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
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":Visitor.AuthState.LOGGED_OUT 
    } 
}); 
```

## Devolución de ID de cliente y estados autenticados {#section-71a610546188478fa9a3185a01d6e83b}

Utilice `getCustomerIDs` para devolver ID de cliente y estados autenticados relacionados. Este método arroja el estado autenticado de un visitante como un número entero.

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

Los ID de cliente y los datos de estado de autenticación arrojados deben tener un aspecto similar a los siguientes ejemplos.

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
  
// setCustomerIDs call on this instance with {"userid":{"authState":Visitor.AuthState.LOGGED_OUT},"dpuuid":{"id":"550e8400-e29b-41d4-a716-446655440000"}} 
{ 
    "userid":{ 
        "authState":2 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":0 
    } 
 }
```

## Compatibilidad con SDK {#section-861c6b3b1ba645dda133dccb22ec7bb0}

El servicio de ID de [!DNL Experience Cloud] admite ID de clientes y estados de autenticación en nuestro código SDK para Android y para iOS. Consulte las bibliotecas de código siguientes:

* [Métodos del SDK para Android](https://experienceleague.adobe.com/docs/mobile-services/android/overview.html?lang=es)
* [Métodos del SDK para iOS](https://experienceleague.adobe.com/docs/mobile-services/ios/overview.html?lang=es)

## Aviso para clientes de Analytics y Audience Manager {#section-3a8e9d51e71c4c6e865184b81ed9d99b}

Si va a pasar ID declarados a [!DNL Audience Manager], el objeto `userid` deberá coincidir con el código de integración asociado a la fuente de datos. Para obtener más información, consulte la sección [!UICONTROL Servicio de ID de visitante] en la documentación [Configurar código de normas de fusión](https://experienceleague.adobe.com/docs/audience-manager/user-guide/features/profile-merge-rules/merge-rules-start.html?lang=es#configure-merge-rule-code).
