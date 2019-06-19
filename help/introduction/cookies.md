---
description: El servicio de ID utiliza su ID de organización, la cookie AMCV de Experience Cloud y una cookie demdex a fin de crear y almacenar identificadores únicos y persistentes para los visitantes de su sitio. Estas cookies permiten que el servicio de ID realice un seguimiento de los visitantes entre los distintos dominios del usuario y permiten compartir datos entre las distintas soluciones de Experience Cloud.
keywords: playstation; Servicio de ID
seo-description: El servicio de ID utiliza su ID de organización, la cookie AMCV de Experience Cloud y una cookie demdex a fin de crear y almacenar identificadores únicos y persistentes para los visitantes de su sitio. Estas cookies permiten que el servicio de ID realice un seguimiento de los visitantes entre los distintos dominios del usuario y permiten compartir datos entre las distintas soluciones de Experience Cloud.
seo-title: Cookies y el servicio de identidad de Experience Platform
title: Cookies y el servicio de identidad de Experience Platform
uuid: c 5 cbd 235-37 ee -4605-8792-b 1 a 991 e 190 ad
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Cookies y el servicio de identidad de Experience Platform{#cookies-and-the-experience-cloud-id-service}

El servicio de ID utiliza su ID de organización, la cookie AMCV de Experience Cloud y una cookie demdex a fin de crear y almacenar identificadores únicos y persistentes para los visitantes de su sitio. Estas cookies permiten que el servicio de ID realice un seguimiento de los visitantes entre los distintos dominios del usuario y permiten compartir datos entre las distintas soluciones de Experience Cloud.

## Información sobre las cookies del servicio de ID {#section-f438168beaec409ab8b2cc58bd021e26}

El servicio de ID depende de las cookies AMCV, AMCVS y demdex para funcionar correctamente. Estas cookies son simplemente archivos que almacenan datos que utiliza el servicio de ID. Estas cookies del servicio de ID no son peligrosas, maliciosas ni distintas de las cookies de origen o de terceros que los sitios web o los servicios almacenan en los navegadores, y siguen las mismas reglas que gobiernan otras cookies de origen o de terceros. Consulte las siguientes secciones para obtener más información sobre las cookies utilizadas por el servicio de ID.

**Qué pueden hacer las cookies del servicio de ID**

* Establecer y almacenar ID únicos para los visitantes del sitio (el MID).
* Conservar este ID único de modo que el servicio de ID pueda recopilar y compartir datos con otras soluciones de Experience Cloud.
* Realizar el seguimiento de los usuarios en sus dominios. Sin embargo, para ello es necesario que usted posea esos otros dominios y que tenga implementado en ellos código del servicio de ID.

** Los ookies del servicio de ID no pueden hacer**

* Almacenar, transmitir o ejecutar virus informáticos.
* Acceder a información de identificación personal (PII), como su dirección de correo electrónico, o bien almacenarla.
* Controlar el hardware o software informático.
* Hacer que los equipos pierdan estabilidad o generar problemas de rendimiento.
* Realizar el seguimiento de los usuarios en sitios que no utilizan el servicio de ID.

## Cookie AMCV {#section-c55af54828dc4cce89f6118655d694c8}

Los atributos siguientes de la cookie configurada por el servicio de ID.

**Nombre**

El nombre de la cookie AMCV sigue la sintaxis `AMCV_<variable name>@AdobeOrg`. En el nombre, `<variable name>` los elementos son marcadores de posición para parte de su ID de organización de Experience Cloud. Este ID se transfiere al DCS mediante la función `Visitor.getInstance` en el código de servicio de ID.

Un nombre de cookie completamente formado tendría un aspecto similar a este:

```
AMCV_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Contenido**

La cookie AMCV contiene el ID de visitante de Experience Cloud o MID. The MID is stored in a key-value pair that follows this syntax, `mid|<Experience Cloud ID>`.

Un par de valor clave completamente formado tendría un aspecto similar a este:

```
mid|20265673158980419722735089753036633573
```

Este identificador persistente permite compartir datos entre soluciones.

**Dominio**

La cookie AMCV se establece en el dominio de origen de un explorador. Es decir, que se establece en el dominio del sitio que está visitando un usuario en ese momento. De este modo, el código del servicio de ID y otras bibliotecas de códigos de Experience Cloud pueden leer el MID almacenado en la cookie AMCV.

No obstante, dado que la cookie AMCV se establece en el dominio de origen, no se puede emplear para seguir e identificar a usuarios entre dominios distintos. En lugar de ello, el servicio de ID se sirve del ID de organización y del ID de demdex para devolver el MID correcto cuando el visitante de un sitio navega a un dominio distinto.

## Cookie AMCVS {#section-92a9454f1ac645948f9059b9fad928bf}

**Nombre**

El nombre de la cookie AMCVS sigue la sintaxis `AMCVS_####@AdobeOrg`. En el nombre, los elementos #### son marcadores de posición para parte de su ID de organización de Experience Cloud. Este ID se transfiere al DCS por `theVisitor.getInstance` función en el código de servicio de ID.

Un nombre de cookie completamente formado tendría un aspecto similar a este:

```
AMCVS_1FD6776A524453CC0A490D44%40AdobeOrg
```

**Contenido**

La cookie AMCVS cookie sirve como indicador de que la sesión se ha inicializado. Su valor siempre es `1` y desaparece cuando la sesión ha finalizado.

**Dominio**

La cookie AMCVS se establece en el dominio de origen de un navegador. Es decir, que se establece en el dominio del sitio que está visitando un usuario en ese momento.

![](assets/AMCVS-cookie.png)

## Cookie demdex {#section-7ff7d96d6e4141b08a84a75a63d7814c}

En la siguiente tabla se enumeran y definen varios atributos importantes de la cookie demdex.

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
   <td colname="col2"> <p>La cookie demdex contiene el ID de demdex, que lo genera el DCS. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Dominio</b> </p> </td> 
   <td colname="col2"> <p>La cookie demdex se establece en el dominio externo demdex.net en el explorador. Este dominio es independiente del sitio que está visitando un usuario en ese momento. </p> <p>A diferencia de la cookie AMCV de origen, la cookie demdex y su ID persisten entre dominios distintos. El ID de demdex y su ID de organización son los valores comunes que permiten al servicio de ID devolver e identificar a un visitante de un sitio con el ID de visitante correcto. </p> </td> 
  </tr> 
 </tbody> 
</table>

Para obtener información relacionada, consulte [Explicación de llamadas al dominio Demdex](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html).

## Generación del Experience Cloud ID {#section-15f69c0bac394b4b9966a23fbc586d17}

El Experience Cloud ID (MID) se deriva matemáticamente de su ID de organización y del ID de demdex. Mientras estos ID permanezcan constantes, generar el MID correcto para un usuario específico es un proceso meramente matemático. Con el mismo ID de organización e ID de demdex, siempre se obtiene el mismo valor MID. Esto permite al servicio de ID realizar un seguimiento de los visitantes entre los dominios que usted controla y ha configurado con el código del servicio de ID.

El servicio de ID empieza a crear un MID mientras se carga su página. Durante este proceso, el código proporcionado por la biblioteca de códigos `visitorAPI.js` envía su ID de organización en una llamada de evento al servicio de ID. El servicio de ID crea y devuelve el MID y un ID de demdex en las cookies AMCV y demdex, respectivamente.

## Pasos siguientes {#section-8db1727a63bc4ff68b495f270315d453}

Consulte [How the Experience Platform Identity Service Requests and Sets IDs…](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a)
