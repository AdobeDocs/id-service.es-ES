---
description: Cambie el nombre de dominio predeterminado utilizado por llamadas al servicio de identidad de Experience Cloud a su propio nombre de subdominio con estas configuraciones.
keywords: Servicio de ID
seo-description: Cambie el nombre de dominio predeterminado utilizado por llamadas al servicio de identidad de Experience Cloud a su propio nombre de subdominio con estas configuraciones.
seo-title: audienceManagerServer y audienceManagerServerSecure
title: audienceManagerServer y audienceManagerServerSecure
uuid: e21cacbf-5151-4d34-b0f7-9e90275f4c7c
translation-type: tm+mt
source-git-commit: e6d65f1bfed187d7440512e8f3c2de0550506c95

---


# audienceManagerServer y audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

Cambie el nombre de dominio predeterminado utilizado por llamadas al servicio de identidad de Experience Cloud a su propio nombre de subdominio con estas configuraciones.

**Sintaxis:**

* ` audienceManagerServer: " *`su nombre de subdominio`*.demdex.net"`
* ` audienceManagerServerSecure: " *`su nombre de subdominio`*.demdex.net"`

**Finalidad**

Normalmente, el servicio de ID de [!DNL Experience Cloud] realiza llamadas a [!DNL Adobe] en `dpm.demdex.net`. A veces, es posible que no desee realizar llamadas a este destino porque parece demasiado genérico o de un "tercero". Para hacer que el servicio de ID se asemeje más a una llamada de origen, utilice estas configuraciones para agregar su nombre de [!DNL Audience Manager] subdominio de a `demdex.net`, como se indica a continuación. Para obtener más información sobre la llamada de `dpm.demdex.net`, consulte [Explicación de las llamadas al dominio Demdex](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html).

**Requisitos**

Para estas configuraciones es necesario que utilice:

* El nombre de [!DNL Audience Manager] subdominio de registro de para su empresa. Verifique u obtenga este nombre de su consultor.
* El nombre de subdominio asociado con su [!DNL Organization ID].
* *Ambos* parámetros de configuración con el nombre de subdominio.

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

