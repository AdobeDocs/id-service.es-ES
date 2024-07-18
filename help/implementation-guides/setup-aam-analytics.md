---
description: Estas instrucciones están destinadas a los clientes de Analytics y Audience Manager que desean utilizar el servicio de identidad de Experience Cloud y no utilizan etiquetas de recopilación de datos. Sin embargo, le recomendamos encarecidamente que utilice etiquetas al implementar el servicio de ID. Las etiquetas optimizan el flujo de trabajo de implementación y garantizan automáticamente la correcta ubicación y secuenciación del código.
keywords: Servicio de ID
title: Implementación del servicio de identidad de Experience Cloud para Analytics y Audience Manager
exl-id: e31720a1-5c89-4084-88f6-443994dbb2f4
source-git-commit: 26152f559150f5bd67d4802b8464446482f2e9a1
workflow-type: tm+mt
source-wordcount: '1183'
ht-degree: 100%

---

# Implementación del servicio de identidad de Experience Cloud para Analytics y Audience Manager{#implement-the-experience-cloud-id-service-for-analytics-and-audience-manager}

Estas instrucciones están destinadas a los clientes de Analytics y Audience Manager que desean utilizar el servicio de identidad de Experience Cloud y no utilizan [etiquetas de recopilación de datos](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=es). Sin embargo, le recomendamos encarecidamente que utilice etiquetas al implementar el servicio de ID. Las etiquetas optimizan el flujo de trabajo de implementación y garantizan automáticamente la correcta ubicación y secuenciación del código.

>[!IMPORTANT]
>
>* [Lea los requisitos](../reference/requirements.md) antes de comenzar.
>* Este procedimiento requiere AppMeasurement. Los clientes que utilizan s_code no pueden completar este procedimiento.
>* Configure y pruebe este código en un entorno de desarrollo antes de implementarlo en producción.

## Paso 1: Planificación del reenvío del lado de servidor {#section-880797cc992d4755b29cada7b831f1fc}

Además de los pasos descritos aquí, los clientes que usan [!DNL Analytics] y [!DNL Audience Manager] deben migrar al reenvío del lado de servidor. El reenvío del lado del servidor permite eliminar DIL (código de recopilación de datos de Audience Manager) y sustituirlo por el [Módulo de Gestión de público](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-other-solutions/audience-management-module.html?lang=es). Consulte la [documentación del reenvío del lado del servidor](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/report-suite-general/server-side-forwarding/ssf.html?lang=es) para obtener más información.

La migración al reenvío del lado del servidor requiere planificación y coordinación. Este proceso incluye cambios externos en el código del sitio y pasos internos que Adobe debe realizar para aprovisionar la cuenta. De hecho, muchos de estos procedimientos de migración deben realizarse en paralelo y ponerse en libertad juntos. La ruta de implementación debe seguir esta secuencia de eventos:

1. Trabaje con sus contactos de [!DNL Analytics] y [!DNL Audience Manager] para planificar el servicio de ID y la migración de reenvío del lado de servidor. Haga que la selección de un servidor de seguimiento conforme una parte importante de este plan.

1. Complete el formulario en el [Sitio de integraciones y aprovisionamiento](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=X8SVES) para empezar.

1. Implementar el servicio de ID y el [!DNL Audience Management Module] simultáneamente. Para que funcione correctamente, el [!DNL Audience Management Module] módulo Gestión de audiencias (reenvío del lado de servidor) y el servicio de ID deben iniciarse para el mismo conjunto de páginas y de forma simultánea.

## Paso 2: Descarga del código del servicio de ID {#section-0780126cf43e4ad9b6fc5fe17bb3ef86}

El servicio de ID requiere la `VisitorAPI.js` biblioteca de códigos. Para descargar esta biblioteca de códigos:

1. Vaya a **[!UICONTROL Administración]** > **[!UICONTROL Administrador de códigos]**.

1. En Administrador de códigos, haga clic en **[!UICONTROL JavaScript (nuevo)]** o **[!UICONTROL JavaScript (heredado)]**. Se descargarán las bibliotecas de códigos comprimidas.

1. Descomprima el archivo de códigos y abra el `VisitorAPI.js` archivo.

## Paso 3: Añadir la función Visitor.getInstance al código del servicio de ID {#section-9e30838b4d0741658a7a492153c49f27}

>[!IMPORTANT]
>
>* Las versiones anteriores de la API de servicio de ID ubicaban esta función en una ubicación diferente y requerían una sintaxis diferente. Si va a realizar la migración desde una versión anterior a la [versión 1.4](../release-notes/notes-2015.md#section-f5c596f355b14da28f45c798df513572), tenga en cuenta la nueva ubicación y sintaxis documentadas aquí.
>* El código en MAYÚSCULAS es un marcador de posición para los valores reales. Reemplace este texto con el identificador de organización, la URL del servidor de seguimiento u otro valor con nombre.

**Parte 1: Copie la función Visitor.getInstance a continuación**

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

**Parte 2: Añadir código de función al archivo API.js de Visitante**

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

**Parte 2: Configurar las variables del servidor de seguimiento**

Para determinar qué variables de servidor de seguimiento utilizar:

1. Responda las preguntas de la matriz de decisión siguiente. Utilice las variables que correspondan a sus respuestas.
1. Reemplace los marcadores de posición del servidor de seguimiento con las direcciones URL del servidor de seguimiento.
1. Elimine las variables del servidor de seguimiento del servidor y de Experience Cloud no utilizadas del código.

![](assets/tracking-server-matrix.png)

>[!NOTE]
>
>Cuando se usen, combine las URL del servidor de Experience Cloud con las URL de su servidor de seguimiento correspondiente de esta manera:

* URL del servidor de Experience Cloud = URL del servidor de seguimiento
* URL segura del servidor de Experience Cloud = URL segura del servidor de seguimiento

Si no está seguro de cómo encontrar su servidor de seguimiento, consulte las [preguntas frecuentes](../faq-intro/faq.md) y [Rellenar correctamente las variables trackingServer y trackingServerSecure](https://helpx.adobe.com/es/analytics/kb/determining-data-center.html#).

## Paso 6: Actualización del archivo AppMeasurement.js {#section-5517e94a09bc44dfb492ebca14b43048}

Este procedimiento requiere [!UICONTROL AppMeasurement]. No podrá continuar si aún utiliza s_code.

Añada la `Visitor.getInstance` función que se muestra a continuación a su `AppMeasurement.js`archivo. Colóquela en la misma sección que contenga configuraciones como `linkInternalFilters`, `charSet`, `trackDownloads`, etc.:

`s.visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");`

>[!IMPORTANT]
>
>En este punto deberá eliminar el código [!DNL Audience Manager] DIL de y sustituirlo por el módulo Gestión de público. Consulte [Implementar reenvío del lado del servidor](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/server-side-forwarding/ssf.html?lang=es) para obtener instrucciones.

***(Opcional, pero recomendada)* Crear una variable prop personalizada.**

Establezca una prop personalizada en `AppMeasurement.js` para medir la cobertura. Agregue esta variable prop personalizada a la `doPlugins` función de su `AppMeasurement.js` archivo:

```js
// prop1 is used as an example only. Choose any available prop. 
s.prop1 = (typeof(Visitor) != "undefined" ? "VisitorAPI Present" : "VisitorAPI Missing");
```

## Paso 7: Añadir el código de API de visitante a la página {#section-c2bd096a3e484872a72967b6468d3673}

Coloque el ` [!UICONTROL VisitorAPI.js]` archivo dentro de las etiquetas `<head>` en cada página. Cuando coloque el `VisitorAPI.js` archivo en su página:

* Hágalo al principio de la `<head>` sección, de modo que aparezca antes que las etiquetas de otras soluciones.
* Debe ejecutarse antes de AppMeasurement y el código de otras soluciones de [!DNL Experience Cloud].

## Paso 8: (Opcional) Configuración de un período de gracia {#section-aceacdb7d5794f25ac6ff46f82e148e1}

Si alguno de estos casos de uso se aplica a su situación, pida al [Servicio de atención al cliente](https://helpx.adobe.com/es/marketing-cloud/contact-support.html) que configure un [periodo de gracia temporal](../reference/analytics-reference/grace-period.md). Los periodos de gracia pueden durar hasta 180 días. Si es necesario, puede renovar un periodo de gracia.

**Implementación parcial**

Necesita un periodo de gracia si dispone de páginas que usan el servicio de ID y otras que no, y todas reportan al mismo grupo de informes de Analytics. Esto es común si tiene un grupo de informes globales que informa entre dominios.

Interrumpa el periodo de gracia después de implementar el servicio de ID en todas las páginas web que informan en el mismo grupo de informes.

**Requisitos de la cookie s_vi**

Necesita un periodo de gracia si necesita nuevos visitantes para tener una cookie s_vi después de migrar al servicio de ID. Esto es común si su implementación lee la cookie s_vi y la almacena en una variable.

Interrumpa el periodo de gracia después de que la implementación pueda capturar el MID en lugar de leer la cookie s_vi.

Consulte también la información relativa a las [Cookies y el servicio de identidad Experience Cloud.](../introduction/cookies.md)

**Integración de flujo de navegación**

Necesita un período de gracia si envía datos a un sistema interno desde una fuente de datos de flujo de navegación y si sus procesos utilizan las columnas `visid_high` y `visid_low`.

Interrumpa el periodo de gracia una vez que su proceso de consumo de datos pueda utilizar las columnas `post_visid_high` y `post_visid_low`.

Consulte [Referencia de columnas de datos del flujo de navegación](https://experienceleague.adobe.com/docs/analytics/export/analytics-data-feed/data-feed-overview.html?lang=es).

## Paso 9: Prueba e implementación del código de servicio de ID {#section-f857542bfc70496dbb9f318d6b3ae110}

Puede realizar pruebas e implementaciones de la siguiente manera.

**Prueba y verificación**

Para probar la implementación del servicio de ID, compruebe:

* [La cookie de AMCV](../introduction/cookies.md) en el dominio en el que está alojada su página.
* Valor MID en la solicitud de imagen de Analytics con [Adobe Debugger](https://experienceleague.adobe.com/docs/analytics/implementation/validate/debugger.html?lang=es).
* Consulte también [Comprobación y verificación del servicio de identidad de Experience Cloud](../implementation-guides/test-verify.md).

Para verificar el reenvío del lado del servidor, consulte [Comprobar la implementación del reenvío del lado del servidor](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/server-side-forwarding/ssf-verify.html?lang=es).

**Implementar**

Implemente el código después de pasar la prueba.

Si habilitó un periodo de gracia:

* Asegúrese de que el ID de Analytics (AID) y el MID estén en la solicitud de imagen.
* Recuerde deshabilitar el período de gracia cuando se cumplan los criterios para ello.
