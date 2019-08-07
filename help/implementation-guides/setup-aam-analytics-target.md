---
description: Estas instrucciones están destinadas a los clientes de Analytics, Audience Manager y Target que desean utilizar el servicio de identidad de Experience Cloud y no usan la administración dinámica de etiquetas (DTM). No obstante, le recomendamos encarecidamente que utilice DTM para implementar el servicio de ID. DTM racionaliza el flujo de trabajo de implementación y garantiza la colocación y secuencia correcta del código automáticamente.
keywords: Servicio de ID
seo-description: Estas instrucciones están destinadas a los clientes de Analytics, Audience Manager y Target que desean utilizar el servicio de identidad de Experience Cloud y no usan la administración dinámica de etiquetas (DTM). No obstante, le recomendamos encarecidamente que utilice DTM para implementar el servicio de ID. DTM racionaliza el flujo de trabajo de implementación y garantiza la colocación y secuencia correcta del código automáticamente.
seo-title: Implementar el servicio de identidad de Experience Cloud para Analytics, Audience Manager y Target
title: Implementar el servicio de identidad de Experience Cloud para Analytics, Audience Manager y Target
uuid: 9d446b77-ca62-4325-8bb0-ff43a52313c0
translation-type: tm+mt
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# Implement the Experience Cloud Identity Service for Analytics, Audience Manager, and Target {#implement-the-experience-cloud-id-service-for-analytics-audience-manager-and-target}

Estas instrucciones están destinadas a los clientes de Analytics, Audience Manager y Target que desean utilizar el servicio de identidad de Experience Cloud y no usan la administración dinámica de etiquetas (DTM). No obstante, le recomendamos encarecidamente que utilice DTM para implementar el servicio de ID. DTM racionaliza el flujo de trabajo de implementación y garantiza la colocación y secuencia correcta del código automáticamente.

>[!IMPORTANT]
>
>Lea los [requisitos](../reference/requirements.md) del servicio de ID antes de empezar y tenga en cuenta los requisitos a continuación que son específicos de esta implementación: &gt;
>* Los clientes que usen s_code no podrán completar este procedimiento. Actualice al código mbox v61 para completar este procedimiento.
>* Configure y pruebe este código en un entorno de desarrollo *antes* de implementarlo en producción.
>



## Paso 1: Planificación del reenvío del lado de servidor {#section-880797cc992d4755b29cada7b831f1fc}

Además de los pasos descritos aquí, los clientes que usan [!DNL Analytics] y [!DNL Audience Manager] deben migrar al reenvío del lado de servidor. El reenvío del lado de servidor permite eliminar el código DIL (el código de recopilación de datos de Audience Manager) y sustituirlo por el [módulo Gestión de público](https://marketing.adobe.com/resources/help/en_US/aam/c_profiles_audiences.html). Consulte la [documentación de reenvío del lado de servidor](https://marketing.adobe.com/resources/help/en_US/reference/ssf.html) para obtener más información.

Migrar al reenvío del lado de servidor requiere planificación y coordinación. Este proceso conlleva realizar cambios externos en el código del sitio, así como determinados pasos internos que Adobe debe implementar para aprovisionar su cuenta. De hecho, muchos de estos procedimientos de migración han de suceder en paralelo e implementarse al mismo tiempo. Su ruta de implementación deberá seguir esta secuencia de eventos:

1. Trabaje con sus contactos de [!DNL Analytics] y [!DNL Audience Manager] para planificar el servicio de ID y la migración de reenvío del lado de servidor. Haga que la selección de un servidor de seguimiento conforme una parte importante de este plan.

1. Complete el formulario en el [sitio de aprovisionamiento e integraciones](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=X8SVES) para ponerse en marcha.

1. Implementar el servicio de ID y el [!DNL Audience Management Module] simultáneamente. Para que funcione correctamente, el [!DNL Audience Management Module]módulo Gestión de audiencias (reenvío del lado de servidor) y el servicio de ID deben iniciarse para el mismo conjunto de páginas y de forma simultánea.

## Paso 2: Descarga del código del servicio de ID {#section-0780126cf43e4ad9b6fc5fe17bb3ef86}

El servicio de ID requiere la `VisitorAPI.js` biblioteca de códigos. Para descargar esta biblioteca de códigos:

1. Vaya a **[!UICONTROL Administración &gt; Administrador de códigos]**.
1. En Administrador de códigos, haga clic en **[!UICONTROL JavaScript (nuevo)]** o **[!UICONTROL JavaScript (heredado)]**. Se descargarán las bibliotecas de códigos comprimidas.

1. Descomprima el archivo de códigos y abra el `VisitorAPI.js` archivo.

## Paso 3: Añadir la función Visitor.getInstance al código del servicio de ID {#section-9e30838b4d0741658a7a492153c49f27}

>[!IMPORTANT]
>
>* Las versiones anteriores de la API del servicio de ID ubicaban esta función en un lugar distinto y requerían una sintaxis diferente. Si va a migrar desde una versión anterior a la [versión 1.4](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572), anote la nueva ubicación y la sintaxis documentadas aquí.
>* El código que aparece TODO EN MAYÚSCULAS funciona como marcador de posición para valores reales. Sustituya este texto por el ID de su organización, la URL del servidor de seguimiento u otro valor con nombre.
>



**Parte 1: Copia de la función Visitor.getInstance a continuación**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

**Parte 2: Adición del código de función al archivo VisitorAPI.js**

Coloque la `Visitor.getInstance` función al final del archivo, después del bloque de códigos. El archivo editado debería tener un aspecto similar a este:

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library 
 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

## Paso 4: Añadir su ID de organización de Experience Cloud a Visitor.getInstance {#section-e2947313492546789b0c3b2fc3e897d8}

En la `Visitor.getInstance` función, sustituya `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` por su ID de organización de Experience Cloud. Si no conoce su ID de organización, puede encontrarlo en la página de administración de Experience Cloud. Su función editada podría tener un aspecto similar al ejemplo siguiente.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*Respete* las mayúsculas y minúsculas de su ID de organización. El ID distingue entre mayúsculas y minúsculas y debe escribirse exactamente como se facilita.

## Paso 5: Añadir sus servidores de seguimiento a Visitor.getInstance {#section-0dfc52096ac2427f86045aab9a0e0dfc}

Analytics utiliza servidores de seguimiento para recopilar datos.

**Parte 1: Búsqueda de las URL de su servidor de seguimiento**

Consulte sus archivos `s_code.js` o `AppMeasurement.js` para buscar las URL del servidor de seguimiento. Buscará las URL especificadas por estas variables:

* `s.trackingServer`
* `s.trackingServerSecure`

**Parte 2: Establecimiento de variables del servidor de seguimiento**

Para determinar las variables del servidor de seguimiento que se van a emplear:

1. Responda las preguntas de la matriz de decisión siguiente. Use las variables que se correspondan con las respuestas.
1. Sustituya los marcadores del servidor de seguimiento por las URL de su servidor de seguimiento.
1. Elimine las variables del servidor de seguimiento y del servidor de Experience Cloud no utilizadas del código.

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>Cuando se usen, combine las URL del servidor de Experience Cloud con las URL de su servidor de seguimiento correspondiente de esta manera:

* URL del servidor de Experience Cloud = URL del servidor de seguimiento
* URL segura del servidor de Experience Cloud = URL segura del servidor de seguimiento

Si no está seguro de cómo encontrar su servidor de seguimiento, consulte las [Preguntas más frecuentes](../faq-intro/faq.md) y [Rellenar correctamente las variables trackingServer y trackingServerSecure](https://helpx.adobe.com/analytics/kb/determining-data-center.html#). 

## Paso 6: Actualización del archivo AppMeasurement.js {#section-5517e94a09bc44dfb492ebca14b43048}

Este paso requiere [!UICONTROL AppMeasurement]. No podrá continuar si aún utiliza s_code.

Añada la `Visitor.getInstance` función que se muestra a continuación a su `AppMeasurement.js`archivo. Colóquela en la misma sección que contenga configuraciones como `linkInternalFilters`, `charSet`, `trackDownloads`, etc.:

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

>[!IMPORTANT]
>
>En este punto deberá eliminar el código [!DNL Audience Manager] DIL de y sustituirlo por el módulo Gestión de audiencias. Consulte las instrucciones en [Implementar el reenvío del lado de servidor](https://marketing.adobe.com/resources/help/en_US/reference/ssf.html).

***(Opcional, pero recomendada)*Crear una variable prop personalizada****

Establezca una prop personalizada en `AppMeasurement.js` para medir la cobertura. Agregue esta variable prop personalizada a la `doPlugins` función de su `AppMeasurement.js` archivo:

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## Paso 7: Añadir el código de API de visitante a la página {#section-c2bd096a3e484872a72967b6468d3673}

Coloque el ` [!UICONTROL VisitorAPI.js]` archivo dentro de las etiquetas `<head>` en cada página. Cuando coloque el `VisitorAPI.js` archivo en su página:

* Hágalo al principio de la `<head>` sección, de modo que aparezca antes que las etiquetas de otras soluciones.
* Debe ejecutarse antes de AppMeasurement y el código de otras [!DNL Experience Cloud] soluciones de.

## Paso 8: (Opcional) Configuración de un período de gracia {#section-aceacdb7d5794f25ac6ff46f82e148e1}

If any of these use cases apply to your situation, ask [Customer Care](https://helpx.adobe.com/marketing-cloud/contact-support.html) to set up a temporary [grace period](../reference/analytics-reference/grace-period.md). Los períodos de gracia pueden prolongarse hasta 180 días. Si es necesario, puede renovar un período de gracia.

**Implementación parcial**

Necesita un período de gracia si hay páginas que usan el servicio de ID y otras no, y si todas envían su informe al mismo grupo de informes de Analytics. Esta suele ser la situación habitual cuando se tiene un grupo de informes global que reporta entre dominios.

Interrumpa el período de gracia una vez que se haya implementado el servicio de ID en todas las páginas web que reportan al mismo grupo de informes.

**Requisitos de la cookie s_vi**

Necesita un período de gracia si necesita que nuevos visitantes tengan una cookie s_vi después de migrar al servicio de ID. Esto es lo habitual si su implementación lee la cookie s_vi y la almacena en una variable.

Interrumpa el período de gracia cuando su implementación pueda capturar el MID en lugar de leer la cookie s_vi.

See also, [Cookies and the Experience Cloud Identity Service](../introduction/cookies.md).

**Integración de flujo de navegación**

Necesita un período de gracia si envía datos a un sistema interno desde una fuente de datos de flujo de navegación y si sus procesos utilizan las columnas `visid_high` y `visid_low`.

Interrumpa el periodo de gracia una vez que su proceso de consumo de datos pueda utilizar las columnas `post_visid_high` y `post_visid_low`.

Consulte también [Referencia de columnas de datos del flujo de navegación](https://marketing.adobe.com/resources/help/en_US/sc/clickstream/datafeeds_reference.html).

## Paso 9: Prueba y verificación {#section-f857542bfc70496dbb9f318d6b3ae110}

Las soluciones de [!DNL Experience Cloud] de esta implementación devuelven ID en forma de pares clave-valor. Cada solución utiliza claves diferentes (p. ej., el [!DNL Analytics] SDID de frente al [!DNL Target] mboxMCSDID de) para guardar el mismo ID. Para probar su implementación, cargue sus páginas en un entorno de desarrollo. Utilice la consola de su navegador o software que permita supervisar las solicitudes y respuestas HTTP para comprobar los ID que aparecen a continuación. El servicio de ID se ha implementado correctamente cuando los pares clave-valor que se enumeran a continuación devuelven los mismos valores de ID.

>[!TIP]
>
>You can use the [Adobe Debugger](https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=debugger.html) or the [Charles HTTP proxy](https://www.charlesproxy.com/) to check for these solution-specific IDs. No obstante, es libre de usar la herramienta o el depurador que más le convenga.

**Todas las soluciones**

Compruebe:

* [La cookie AMCV](../introduction/cookies.md) en el dominio en el que está alojada su página.
* El ID de [!DNL Experience Cloud] (MID) con la herramienta de depuración de [!DNL Adobe] o su herramienta de depuración favorita.

For additional checks that help you determine if the ID service is working properly, see [Test and Verify the Experience Cloud Identity Service](../implementation-guides/test-verify.md).

**Analytics**

Compruebe el identificador SDID en la solicitud de JavaScript. El SDID de Analytics debe coincidir con el mboxMCSDID de Target.

Si sus pruebas devuelven un AID, será indicativo de alguna de estas situaciones:

* Usted es un visitante que regresa en el proceso de migrar [!DNL Analytics] ID de heredados.
* Tiene un [período de gracia](../reference/analytics-reference/grace-period.md) habilitado.

Si ve un AID, compare su valor con el [!DNL Target] mboxMCAVID de. Estos valores son idénticos cuando el servicio de ID se ha implementado correctamente.

**Audience Manager**

Para probar el reenvío del lado de servidor, consulte:

* [Cómo determinar si su cuenta está lista para recibir datos reenviados](https://marketing.adobe.com/resources/help/en_US/aam/ssf-success.html)
* [Cómo determinar si su cuenta no está lista para recibir datos reenviados](https://marketing.adobe.com/resources/help/en_US/aam/ssf-fail.html)

**Target**

Compruebe:

* mboxMCGVID
* mboxMCSDID (el mboxMCSDID debe coincidir con el SDID de Analytics)

Si sus pruebas devuelven un mboxMCAVID, será indicativo de alguna de estas situaciones:

* Usted es un visitante que regresa en el proceso de migrar [!DNL Analytics] ID de heredados.
* Tiene un período de gracia habilitado.

Si ve un mboxMCAVID, compare su valor con el [!DNL Analytics] AID de. Estos valores son idénticos cuando el servicio de ID se ha implementado correctamente.

**Implementación**

## Paso 10: Implementación {#section-4188fa95e7dc455a986b48a6c517c1c9}

Implementación del código una vez pasada la prueba.

Si ha habilitado un período de gracia:

* Asegúrese de que el ID de Analytics (AID) y el MID estén en la solicitud de imagen.
* Recuerde deshabilitar el período de gracia cuando se cumplan los [criterios para ello](../implementation-guides/setup-aam-analytics-target.md#section-aceacdb7d5794f25ac6ff46f82e148e1).

