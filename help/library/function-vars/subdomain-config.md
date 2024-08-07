---
description: Cambiar el nombre de dominio predeterminado utilizado por las llamadas al servicio de identidad de Experience Cloud por el de su propio nombre de subdominio con estas configuraciones.
keywords: Servicio de ID
title: audienceManagerServer y audienceManagerServerSecure
exl-id: b740eb5c-ac4e-46f4-ba7c-1080d8d9292d
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 100%

---

# audienceManagerServer y audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

Cambiar el nombre de dominio predeterminado utilizado por las llamadas al servicio de identidad de Experience Cloud por el de su propio nombre de subdominio con estas configuraciones.

**Sintaxis:**

* ` audienceManagerServer: " *`su nombre de subdominio`*.demdex.net"`
* ` audienceManagerServerSecure: " *`su nombre de subdominio`*.demdex.net"`

**Finalidad**

Normalmente, el servicio de ID de [!DNL Experience Cloud] realiza llamadas a [!DNL Adobe] en `dpm.demdex.net`. A veces, es posible que no desee realizar llamadas a este destino porque parece demasiado genérico o de un &quot;tercero&quot;. Para hacer que el servicio de ID se asemeje más a una llamada de origen, utilice estas configuraciones para agregar su nombre de [!DNL Audience Manager] subdominio de a `demdex.net`, como se indica a continuación. Para obtener más información sobre la llamada a `dpm.demdex.net`, consulte [Explicación de las llamadas a Demdex Domain](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=es).

**Requisitos**

Estas configuraciones requieren que utilice:

* El nombre de [!DNL Audience Manager] subdominio de registro de para su empresa. Verifique u obtenga este nombre de su consultor.
* El nombre de subdominio asociado con su [!UICONTROL ID de organización].
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
