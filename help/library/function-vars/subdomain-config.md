---
description: Cambiar el nombre de dominio predeterminado utilizado por las llamadas al servicio de ID de visitante por el de su propio nombre de subdominio con estas configuraciones.
keywords: Servicio de ID de visitante
title: audienceManagerServer y audienceManagerServerSecure
exl-id: b740eb5c-ac4e-46f4-ba7c-1080d8d9292d
TQID: https://experienceleague.adobe.com/a5KVErDX4putY8d9vGf-uAwswNzE0Maf-JEyfmQxhbg
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 234
ht-degree: 44%

---

# audienceManagerServer y audienceManagerServerSecure{#audiencemanagerserver-and-audiencemanagerserversecure}

Cambiar el nombre de dominio predeterminado utilizado por las llamadas al servicio de ID de visitante por el de su propio nombre de subdominio con estas configuraciones.

**Sintaxis:**

* `audienceManagerServer: " *`su nombre de subdominio`*.demdex.net"`
* `audienceManagerServerSecure: " *`su nombre de subdominio`*.demdex.net"`

**Finalidad**

Normalmente, el servicio de ID de visitante realiza llamadas a Adobe en `dpm.demdex.net`. A veces, es posible que no desee realizar llamadas a este destino porque parece demasiado genérico o de un &quot;tercero&quot;. Para hacer que el servicio de identificación del visitante se asemeje más a una llamada de origen, use estas configuraciones para agregar su nombre de subdominio de Audience Manager a `demdex.net`, como se muestra a continuación. Para obtener más información sobre la llamada a `dpm.demdex.net`, consulte [Explicación de las llamadas a Demdex Domain](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=es).

**Requisitos**

Estas configuraciones requieren que utilice:

* El nombre de registro del subdominio de Audience Manager de su empresa. Verifique u obtenga este nombre de su consultor.
* El nombre de subdominio asociado con su ID de organización de IMS.
* *Ambos* parámetros de configuración con el mismo nombre de subdominio.

**Ejemplo de código**

En este ejemplo, supongamos que tenemos una empresa de dispositivos multimedia y de entretenimiento que ha expresado dudas legales realizando llamadas a `dpm.demdex.net`. En Audience Manager, el nombre de registro de subdominio de empresa es Music1. En el siguiente ejemplo de código se muestra cómo asignar una marca a la llamada de datos del servicio de ID de visitante con este nombre de subdominio específico del cliente.

```
//Instantiate Visitor 
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE",{ 
     ... 
     //Configure Visitor ID Service call 
     audienceManagerServer: "Music1.demdex.net", 
     audienceManagerServerSecure: "Music1.demdex.net" 
     } 
);
```

