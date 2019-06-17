---
description: Cambian el nombre de dominio predeterminado utilizado por las llamadas al servicio Experience Cloud ID por el de su propio nombre de subdominio con estas configuraciones.
keywords: Servicio de ID
seo-description: Cambian el nombre de dominio predeterminado utilizado por las llamadas al servicio Experience Cloud ID por el de su propio nombre de subdominio con estas configuraciones.
seo-title: audienceManagerServer y audienceManagerServerSecure
title: audienceManagerServer y audienceManagerServerSecure
uuid: e 21 cacbf -5151-4 d 34-b 0 f 7-9 e 90275 f 4 c 7 c
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# audienceManagerServer y audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

Cambian el nombre de dominio predeterminado utilizado por las llamadas al servicio Experience Cloud ID por el de su propio nombre de subdominio con estas configuraciones.

**Sintaxis:**

* ` audienceManagerServer: " *`su nombre de subdominio`*.demdex.net"`
* ` audienceManagerServerSecure: " *`su nombre de subdominio`*.demdex.net"`

**Finalidad**

Normalmente, [!DNL Experience Cloud] el servicio de ID llama a [!DNL Adobe] at `dpm.demdex.net`. A veces, es posible que no desee realizar llamadas a este destino porque parece demasiado genérico o de un &quot;tercero&quot;. Para hacer que el servicio de ID se asemeje más a una llamada de origen, utilice estas configuraciones para agregar su nombre de subdominio de [!DNL Audience Manager] a `demdex.net`, como se indica a continuación. Para obtener más información sobre la llamada de `dpm.demdex.net`, consulte [Explicación de las llamadas al dominio Demdex](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html).

**Requisitos**

Para estas configuraciones es necesario que utilice:

* Nombre [!DNL Audience Manager] de subdominio de registro para su empresa. Verifique u obtenga este nombre de su consultor.
* El nombre de subdominio asociado a [!DNL Organization ID]su.
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

