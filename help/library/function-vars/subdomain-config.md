---
description: Cambiar el nombre de dominio predeterminado utilizado por las llamadas al servicio de identidad de Experience Cloud por el de su propio nombre de subdominio con estas configuraciones.
keywords: ID Service
seo-description: Cambiar el nombre de dominio predeterminado utilizado por las llamadas al servicio de Experience Cloud ID por el de su propio nombre de subdominio con estas configuraciones.
seo-title: audienceManagerServer y audienceManagerServerSecure
title: audienceManagerServer y audienceManagerServerSecure
uuid: e21cacbf-5151-4d34-b0f7-9e90275f4c7c
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# audienceManagerServer y audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

Cambiar el nombre de dominio predeterminado utilizado por las llamadas al servicio de Experience Cloud ID por el de su propio nombre de subdominio con estas configuraciones.

**Sintaxis:**

* ` audienceManagerServer: " *`su nombre de subdominio`*.demdex.net"`
* ` audienceManagerServerSecure: " *`su nombre de subdominio`*.demdex.net"`

**Finalidad**

Normalmente, el servicio de ID de [!DNL Experience Cloud] realiza llamadas a [!DNL Adobe] en `dpm.demdex.net`. A veces, es posible que no desee realizar llamadas a este destino porque parece demasiado genérico o de un &quot;tercero&quot;. Para hacer que el servicio de ID se asemeje más a una llamada de origen, utilice estas configuraciones para agregar su nombre de [!DNL Audience Manager] subdominio de a `demdex.net`, como se indica a continuación. For more information about the `dpm.demdex.net` call, see [Understanding Calls to the Demdex Domain](https://docs.adobe.com/content/help/es-ES/audience-manager/user-guide/reference/demdex-calls.html).

**Requisitos**

Estas configuraciones requieren que utilice:

* El nombre de [!DNL Audience Manager] subdominio de registro de para su empresa. Verifique u obtenga este nombre de su consultor.
* The subdomain name associated with your [!UICONTROL Organization ID].
* *Ambos* parámetros de configuración con el mismo nombre de subdominio.

**Ejemplo de código**

En este ejemplo, supongamos que tenemos una empresa de dispositivos multimedia y de entretenimiento que ha expresado dudas legales realizando llamadas a `dpm.demdex.net`. En [!DNL Audience Manager], el nombre de registro de subdominio de empresa es Music1. El código de ejemplo siguiente demuestra cómo asignar una marca a la llamada de datos de servicio de ID con este nombre de subdominio específico del cliente.

```
//Instantiate Visitor 
var visitor = Visitor.getInstance("Insert Experience Cloud Organization ID here",{ 
     ... 
     //Configure ID service call 
     audienceManagerServer: "Music1.demdex.net", 
     audienceManagerServerSecure: "Music1.demdex.net" 
     } 
);
```

