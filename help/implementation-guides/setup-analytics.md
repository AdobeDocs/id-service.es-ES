---
description: Estas instrucciones están destinadas a los clientes de Analytics que desean utilizar el servicio de identidad de Experience Cloud y no utilizan Dynamic Tag Management (DTM). No obstante, le recomendamos encarecidamente que utilice DTM para implementar el servicio de ID. DTM racionaliza el flujo de trabajo de implementación y garantiza la colocación y secuencia correcta del código automáticamente.
keywords: Servicio de ID
seo-description: Estas instrucciones están destinadas a los clientes de Analytics que desean utilizar el servicio de Experience Cloud ID y no utilizan Dynamic Tag Management (DTM). No obstante, le recomendamos encarecidamente que utilice DTM para implementar el servicio de ID. DTM racionaliza el flujo de trabajo de implementación y garantiza la colocación y secuencia correcta del código automáticamente.
seo-title: Implementación del servicio de identidad de Experience Cloud para Analytics
title: Implementación del servicio de Experience Cloud ID para Analytics
uuid: 7fbd6fa0-1713-4232-8680-500ed62709d5
translation-type: ht
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# Implementación del servicio de identidad de Experience Cloud para Analytics {#implement-the-experience-cloud-id-service-for-analytics}

Estas instrucciones están destinadas a los clientes de Analytics que desean utilizar el servicio de Experience Cloud ID y no utilizan Dynamic Tag Management (DTM). No obstante, le recomendamos encarecidamente que utilice DTM para implementar el servicio de ID. DTM racionaliza el flujo de trabajo de implementación y garantiza la colocación y secuencia correcta del código automáticamente.

>[!IMPORTANT]
>
>* [Lea los requisitos](../reference/requirements.md) antes de comenzar.
>* Configure y pruebe este código en un entorno de desarrollo antes de implementarlo en producción.
>



Siga estos pasos para implementar el servicio de ID para Adobe Analytics:

1. [Descarga del código del servicio de ID](../implementation-guides/setup-analytics.md#section-ead9403a6b7e45b887f9ac959ef89f7f)
1. [Añadir la función Visitor.getInstance al código de servicio de ID](../implementation-guides/setup-analytics.md#section-6053a6b7c16c466a9f9fdbf9cb9db3df)
1. [Añadir su ID de organización de Experience Cloud a Visitor.getInstance](../implementation-guides/setup-analytics.md#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e)
1. [Añadir sus servidores de seguimiento a Visitor.getInstance.](../implementation-guides/setup-analytics.md#section-70ec9ebff47940d8ab520be5ec4728c5)
1. [Actualización de su archivo AppMeasurement.js o s_code.js](../implementation-guides/setup-analytics.md#section-b53113aea1bd4de896e0e4e9a7edee19)
1. [Añadir el código de API de visitante a la página](../implementation-guides/setup-analytics.md#section-d46d6aa324c842f2931d901e38d6db1d)
1. [(Opcional) Configurar un periodo de gracia](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3)
1. [Prueba e implementación del código de servicio de ID](../implementation-guides/setup-analytics.md#section-e9c1764ac21a4ec5be1ff338c0e2e01b)

## Paso 1: Descarga del código del servicio de ID {#section-ead9403a6b7e45b887f9ac959ef89f7f}

El [!UICONTROL servicio de ID] requiere la biblioteca de códigos `VisitorAPI.js`. Para descargar esta biblioteca de códigos:

1. Vaya a **[!UICONTROL Administración]** &gt; **[!UICONTROL Administrador de códigos]**.
1. En [!UICONTROL Administrador de códigos], haga clic en **[!UICONTROL JavaScript (nuevo)]** o **[!UICONTROL JavaScript (heredado)]**.

   Se descargarán las bibliotecas de códigos comprimidas.

1. Descomprima el archivo de códigos y abra el `VisitorAPI.js` archivo.

## Paso 2: Añadir la función Visitor.getInstance al código de servicio de ID {#section-6053a6b7c16c466a9f9fdbf9cb9db3df}

>[!IMPORTANT]
>
>* Las versiones anteriores de la API del servicio de ID ubicaban esta función en un lugar distinto y requerían una sintaxis diferente. Si va a migrar desde una versión anterior a la [versión 1.4](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572), anote la nueva ubicación y la sintaxis documentadas aquí.
>* El código que aparece TODO EN MAYÚSCULAS funciona como marcador de posición para valores reales. Sustituya este texto por el ID de su organización, la URL del servidor de seguimiento u otro valor con nombre.
>



**Parte 1: Copia de la función Visitor.getInstance a continuación**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
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

var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
}); 
```

## Paso 3: Añadir su ID de organización de Experience Cloud a Visitor.getInstance {#section-7b8a6e76dc124d0e9ab1ce96ab2ffb0e}

En la `Visitor.getInstance` función, sustituya `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` por su [!DNL Experience Cloud] ID de organización de. Si no conoce su ID de organización, puede encontrarlo en la página de administración de[!DNL Experience Cloud]. Consulte también [Administración - Servicios principales](https://marketing.adobe.com/resources/help/es_ES/mcloud/admin_getting_started.html). Su función editada podría tener un aspecto similar al ejemplo siguiente.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg", { ...`

>[!IMPORTANT]
>
>*Respete* las mayúsculas y minúsculas de su ID de organización. El ID distingue entre mayúsculas y minúsculas y debe escribirse exactamente como se facilita.

## Paso 4: Añadir sus servidores de seguimiento a Visitor.getInstance {#section-70ec9ebff47940d8ab520be5ec4728c5}

Los servidores de seguimiento se emplean para la recopilación de datos de [!DNL Analytics].

**Parte 1: Búsqueda de las URL de su servidor de seguimiento**

Consulte sus archivos `s_code.js` o `AppMeasurement.js` para buscar las URL del servidor de seguimiento. Buscará las URL especificadas por estas variables:

* `s.trackingServer`
* `s.trackingServerSecure`

**Parte 2: Establecimiento de variables del servidor de seguimiento**

Para determinar las variables del servidor de seguimiento que se van a emplear:

1. Responda las preguntas de la matriz de decisión siguiente. Use las variables que se correspondan con las respuestas.
1. Sustituya los marcadores del servidor de seguimiento por las URL de su servidor de seguimiento.
1. Elimine las variables del servidor de seguimiento y del [!DNL Experience Cloud] servidor de no utilizadas del código.

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>Cuando se usen, combine las [!DNL Experience Cloud] URL del servidor de con las URL de su servidor de seguimiento correspondiente de esta manera: &gt;
>* [!DNL Experience Cloud]URL del servidor de = URL del servidor de seguimiento
>* [!DNL Experience Cloud]URL segura del servidor de = URL segura del servidor de seguimiento
>



Si no está seguro de cómo encontrar su servidor de seguimiento, consulte [las preguntas frecuentes](../faq-intro/faq.md) y [Rellenar correctamente las variables trackingServer y trackingServerSecure](https://helpx.adobe.com/es/analytics/kb/determining-data-center.html#).

## Paso 5: Actualización de su archivo AppMeasurement.js o s_code.js {#section-b53113aea1bd4de896e0e4e9a7edee19}

Añada esta función a su archivo `AppMeasurement.js` o `s_code.js`:

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

Coloque el código en la misma sección que contenga configuraciones como `linkInternalFilters`, `charSet`, `trackDownloads`, etc.

***(Opcional, pero recomendada)*Cree una variable prop personalizada****

Configurar una variable prop personalizada en `AppMeasurement.js` o `s_code.js` para medir la cobertura. Añada esta variable prop personalizada a la `doPlugins` función de sus archivos `AppMeasurement.js` o `s_code.js`:

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## Paso 6: Añadir el código de API de visitante a la página {#section-d46d6aa324c842f2931d901e38d6db1d}

Coloque el `VisitorAPI.js` archivo dentro de las etiquetas `<head>` en cada página. Cuando coloque el `VisitorAPI.js` archivo en su página:

* Hágalo al principio de la `<head>` sección, de modo que aparezca antes que las etiquetas de otras soluciones.
* Debe ejecutarse antes de AppMeasurement y el código de otras soluciones de [!DNL Experience Cloud].

Mueva este código a producción después de la prueba y verificación.

## Paso 7: (Opcional) Configuración de un período de gracia {#section-7bbb2f72c26e4abeb8881e18366797a3}

Si alguno de estos casos de uso se aplica a su situación, pida al [Servicio de atención al cliente](https://helpx.adobe.com/es/marketing-cloud/contact-support.html) que configure un [periodo de gracia temporal](../reference/analytics-reference/grace-period.md). Los períodos de gracia pueden prolongarse hasta 180 días. Si es necesario, puede renovar un período de gracia.

**Implementación parcial**

Necesita un período de gracia si dispone de páginas que usan el servicio de ID y otras que no, y todas reportan al mismo grupo de [!DNL Analytics] informes de. Esta suele ser la situación habitual cuando se tiene un grupo de informes global que reporta entre dominios.

Interrumpa el período de gracia una vez que se haya implementado el servicio de ID en todas las páginas web que reportan al mismo grupo de informes.

**Requisitos de la cookie s_vi**

Necesita un período de gracia si necesita que nuevos visitantes tengan una cookie s_vi después de migrar al servicio de ID. Esto es lo habitual si su implementación lee la cookie s_vi y la almacena en una variable.

Interrumpa el período de gracia cuando su implementación pueda capturar el MID en lugar de leer la cookie s_vi.

Consulte [Cookies y el servicio de identidad de Experience Cloud](../introduction/cookies.md).

Necesita un período de gracia si envía datos a un sistema interno desde una fuente de datos de flujo de navegación y si sus procesos utilizan las columnas `visid_high` y `visid_low`.

Interrumpa el periodo de gracia una vez que su proceso de consumo de datos pueda utilizar las columnas `post_visid_high` y `post_visid_low`.

Consulte la información sobre la [Columna de datos de flujo de navegación](https://marketing.adobe.com/resources/help/es_ES/sc/clickstream/datafeeds_reference.html).

**Consumo de datos de flujo de navegación**

## Paso 8: Prueba e implementación del código de servicio de ID {#section-e9c1764ac21a4ec5be1ff338c0e2e01b}

Puede realizar pruebas e implementaciones de la siguiente manera.

**Prueba y verificación**

Para probar la implementación del servicio de ID, compruebe:

* La [cookie AMCV](../introduction/cookies.md) en el dominio en el que está alojada su página.
* Valor MID en la solicitud de imagen de [!DNL Analytics] con [Adobe Debugger](https://marketing.adobe.com/resources/help/es_ES/sc/implement/debugger.html).

Consulte [Comprobación y verificación del servicio de identidad de Experience Cloud](../implementation-guides/test-verify.md).

**Implementación de código**

Implementación del código una vez pasada la prueba.

Si ha habilitado un período de gracia en el [Paso 7](../implementation-guides/setup-analytics.md#section-7bbb2f72c26e4abeb8881e18366797a3):

* Asegúrese de que el [!DNL Analytics] ID de (AID) y el MID estén en la solicitud de imagen.
* Recuerde deshabilitar el período de gracia cuando se cumplan los criterios para ello.
