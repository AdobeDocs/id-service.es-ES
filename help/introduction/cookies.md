---
description: El servicio de ID de visitante utiliza su ID de organización de IMS, la cookie AMCV de CX Enterprise y una cookie demdex a fin de crear y almacenar ID únicos y persistentes para los visitantes de su sitio. Estas cookies permiten que el servicio de ID de visitante realice un seguimiento de los visitantes entre los distintos dominios del usuario y permiten compartir datos entre las distintas soluciones de CX Enterprise.
keywords: playstation;Servicio de ID de visitante
title: Cookies y el servicio de ID de visitante de Adobe
exl-id: 727c6381-56b9-44b8-8e59-355d072769be
TQID: https://experienceleague.adobe.com/iLOFGQ9t-DqYfqOZs3K5yZI7903dMPEjANaJ7lH8K0o
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 990
ht-degree: 42%

---

# Cookies y el servicio de ID de visitante de Adobe{#cookies-and-the-experience-cloud-id-service}

El servicio de ID de visitante utiliza su ID de organización de IMS, la cookie AMCV de CX Enterprise y una cookie demdex a fin de crear y almacenar ID únicos y persistentes para los visitantes de su sitio. Estas cookies permiten que el servicio de ID de visitante realice un seguimiento de los visitantes entre los distintos dominios del usuario y permiten compartir datos entre las distintas soluciones de CX Enterprise.

## Explicación de las cookies del servicio de ID de visitante {#section-f438168beaec409ab8b2cc58bd021e26}

El servicio de ID de visitante se basa en las cookies AMCV, AMCVS y demdex para funcionar correctamente. Estas cookies son solo archivos que almacenan datos utilizados por el servicio de ID de visitante. Estas cookies del servicio de ID de visitante no son peligrosas, maliciosas ni diferentes de otras cookies de origen o de terceros almacenadas por un sitio web o servicio en un explorador, siguiendo las mismas reglas que rigen otras cookies de origen y de terceros. Consulte las secciones siguientes para obtener más información sobre las cookies que utiliza el servicio de ID de visitante.

### Qué pueden hacer las cookies del servicio de ID de visitante

* Configure y almacene un ID único para los visitantes del sitio (el MID).
* Mantenga este ID único para que el servicio de ID de visitante pueda recopilar y compartir datos con otras soluciones de CX para empresas.
* Rastree a los usuarios en sus dominios. Sin embargo, esto requiere que sea propietario de esos otros dominios y que tenga implementado el código del servicio de ID de visitante.

### Qué no pueden hacer las cookies del servicio de ID de visitante

* Almacenar, transmitir o ejecutar virus informáticos.
* Acceda o almacene información de identificación personal (PII) como su dirección de correo electrónico.
* Controlar el hardware o software del equipo.
* Hacer que los equipos sean inestables o causen problemas de rendimiento.
* Rastree a los usuarios en sitios que no utilicen el servicio de ID de visitante.

## Cookie AMCV {#section-c55af54828dc4cce89f6118655d694c8}

Los atributos siguientes de la cookie configurada por el servicio de ID de visitante.

**Nombre**

El nombre de la cookie AMCV sigue la sintaxis `AMCV_<variable name>@AdobeOrg`. En el nombre, los elementos `<variable name>` son marcadores de posición para parte de su ID de organización de IMS. Este ID se pasa al DCS mediante la función `Visitor.getInstance` en el código del servicio de ID de visitante.

Un nombre de cookie completamente formado tendría un aspecto similar a este:

```
AMCV_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Contenido**

La cookie AMCV contiene el ECID o MID. El MID se almacena en un par de clave-valor que sigue esta sintaxis, `MCMID|<ECID>`.

Un par de valor clave completamente formado tendría un aspecto similar a este:

```
MCMID|20265673158980419722735089753036633573
```

Este identificador persistente permite el uso compartido de datos entre soluciones.

**Dominio**

La cookie AMCV se establece en el dominio de origen de un explorador. Esto significa que se establece en el dominio del sitio que un usuario visita actualmente. De este modo, el código del servicio de ID de visitante y otras bibliotecas de código empresarial de CX pueden leer el MID almacenado en la cookie AMCV.

Sin embargo, dado que la cookie AMCV se establece en el dominio de origen, no se puede utilizar para rastrear e identificar a los usuarios en distintos dominios. En su lugar, el servicio de ID de visitante se basa en el ID de organización de IMS y el ID de demdex para devolver el MID correcto cuando un visitante del sitio navega a un dominio diferente.

## Cookie AMCVS {#section-92a9454f1ac645948f9059b9fad928bf}

**Nombre**

El nombre de la cookie AMCVS sigue la sintaxis `AMCVS_####@AdobeOrg`. En el nombre, los elementos #### son marcadores de posición para parte de su ID de organización de IMS. Este ID se transfiere al DCS mediante la función `theVisitor.getInstance` en el código del servicio de ID de visitante.

Un nombre de cookie completamente formado tendría un aspecto similar a este:

```
AMCVS_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Contenido**

La cookie AMCVS sirve como un indicador que indica que la sesión se ha inicializado. Su valor siempre es `1`, y se interrumpe cuando la sesión termina.

**Dominio**

La cookie AMCVS se establece en el dominio de origen de un explorador. Esto significa que se establece en el dominio del sitio que un usuario visita actualmente.

![](assets/AMCVS-cookie.png)

## Cookie demdex {#section-7ff7d96d6e4141b08a84a75a63d7814c}

La siguiente tabla muestra y define algunos atributos importantes de la cookie demdex.

<table id="table_18E3CAF3550E4BB6A199736AACE39202"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Atributo </th> 
   <th colname="col2" class="entry"> Descripción </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Nombre</b> </p> </td> 
   <td colname="col2"> <p>El nombre de la cookie es “demdex”. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Contenido</b> </p> </td> 
   <td colname="col2"> <p>La cookie demdex contiene el ID de demdex, que genera el DCS. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Dominio</b> </p> </td> 
   <td colname="col2"> <p>La cookie demdex se establece en el dominio de terceros demdex.net en el explorador. Este dominio es independiente del sitio que actualmente visita un usuario. </p> <p>A diferencia de la cookie AMCV de origen, la cookie demdex y el ID persisten en distintos dominios. El ID de demdex y el ID de organización de IMS son los valores comunes que permiten al servicio de ID de visitante devolver e identificar un visitante de sitio con el ID de visitante correcto. </p> </td> 
  </tr> 
 </tbody> 
</table>

Para obtener información sobre las divulgaciones relativas a Demdex, visite las [divulgaciones del almacenamiento de dispositivos de Audience Manager](https://aam-iab-tcf-vendor.s3.amazonaws.com/aam_device_storage_disclosures.json).

Para obtener información relacionada, lea la documentación sobre la [explicación de las llamadas al dominio Demdex](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=es).

## Generación del ECID {#section-15f69c0bac394b4b9966a23fbc586d17}

El ECID se deriva matemáticamente de su ID de organización de IMS y del ID de demdex. Mientras estos ID permanezcan constantes, la generación del MID adecuado para un usuario específico es simplemente un problema matemático. Con el mismo ID de organización de IMS e ID de demdex, se obtiene el mismo valor de MID cada vez. Esto permite que el servicio de ID de visitante rastree los visitantes entre dominios que controla y que ha configurado con el código del servicio de ID de visitante.

El servicio de ID de visitante empieza a crear un MID a medida que se carga la página. Durante este proceso, el código proporcionado por la biblioteca de códigos `VisitorAPI.js` envía su ID de organización de IMS en una llamada de evento al servicio de ID de visitante. El servicio de ID de visitante crea y devuelve el MID y un ID de demdex en las cookies AMCV y demdex, respectivamente.

## Indicadores de cookies

En la tabla siguiente se describen los indicadores de las cookies de CX Enterprise:

| Cookie (establecida por) | httpOnly | Secure | SameSite |
|--- |--- |--- |--- |
| demdex (respuesta http) | No | Sí | &quot;Ninguno&quot; |
| AMCV (JavaScript) | No | Configurable | Unset (predeterminado en Lax) |
| AMCVS (JavaScript) | No | Configurable | Unset (predeterminado en Lax) |

*Nota: Para obtener información sobre la configuración de las cookies AMCV y AMCVS con atributos seguros, consulte [secureCookie](../library/function-vars/securecookie.md).*

## Próximos pasos {#section-8db1727a63bc4ff68b495f270315d453}

Ver [Solicitud y configuración de ID con el servicio de ID de visitante...](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a).

