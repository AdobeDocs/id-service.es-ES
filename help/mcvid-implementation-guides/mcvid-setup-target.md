---
description: Estas instrucciones están destinadas a los clientes de Target que desean utilizar el servicio Experience Cloud ID y no utilizan Dynamic Tag Management (DTM). No obstante, le recomendamos encarecidamente que utilice DTM para implementar el servicio de ID. DTM racionaliza el flujo de trabajo de implementación y garantiza la colocación y secuencia correcta del código automáticamente.
keywords: Servicio de ID
seo-description: Estas instrucciones están destinadas a los clientes de Target que desean utilizar el servicio Experience Cloud ID y no utilizan Dynamic Tag Management (DTM). No obstante, le recomendamos encarecidamente que utilice DTM para implementar el servicio de ID. DTM racionaliza el flujo de trabajo de implementación y garantiza la colocación y secuencia correcta del código automáticamente.
seo-title: Implementación del servicio Experience Cloud ID para Target
title: Implementación del servicio Experience Cloud ID para Target
uuid: cb 3581 fa -4 c 4 b -43 aa-bb 8 e -8 db 85 a 6 a 1 ef 2
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Implementación del servicio Experience Cloud ID para Target{#implement-the-experience-cloud-id-service-for-target}

Estas instrucciones están destinadas a los clientes de Target que desean utilizar el servicio Experience Cloud ID y no utilizan Dynamic Tag Management (DTM). No obstante, le recomendamos encarecidamente que utilice DTM para implementar el servicio de ID. DTM racionaliza el flujo de trabajo de implementación y garantiza la colocación y secuencia correcta del código automáticamente.

>[!IMPORTANT]
>
>* [Lea los requisitos](../mcvid-reference/mcvid-requirements.md) antes de comenzar.
>* Configure y pruebe este código en un entorno de desarrollo antes de implementarlo en producción.
>



## Paso 1: Obtener el código del servicio de ID {#section-b32ba0548aa546a79dd38be59832a53e}

[!DNL ID Service] La biblioteca de `VisitorAPI.js` código requiere. Contacte con el [Servicio de atención al cliente](https://helpx.adobe.com/marketing-cloud/contact-support.html) para obtener este código.

## Paso 2: Agregar la función Visitor. getinstance al código del servicio de ID {#section-287ef2958e9f43858fe9d630ae519e22}

**Parte 1: Copia de la función Visitor.getInstance a continuación**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE"); 
```

**Parte 2: Adición del código de función al archivo VisitorAPI.js**

Coloque la función `Visitor.getInstance` al final del archivo, después del bloque de códigos. El archivo editado debería tener un aspecto similar a este:

```js
/* 
========== DO NOT ALTER ANYTHING BELOW THIS LINE ========== 
Version and copyright section 
*/ 
 
// Visitor API code library section 
 
// Put Visitor.getInstance at the end of the file, after the code library 
 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE");
```

## Paso 3: Add your Experience Cloud Organization ID to Visitor. getinstance {#section-522b1877be9243c39b222859b821f0ce}

En la `Visitor.getInstance` función, reemplace `INSERT-MARKETING-CLOUD-ORGANIZATION ID-HERE` por su ID [!DNL Experience Cloud] de organización. Si no conoce su ID de organización, puede encontrarlo en la página de administración de [!DNL Experience Cloud]. Consulte también [Administración - Servicios principales](https://marketing.adobe.com/resources/help/en_US/mcloud/admin_getting_started.html). Su función editada podría tener un aspecto similar al ejemplo siguiente.

`var visitor = Visitor.getInstance("1234567ABC@AdobeOrg");`

>[!IMPORTANT]
>
>*No* cambie el caso de los caracteres del identificador de organización. El ID distingue entre mayúsculas y minúsculas y debe escribirse exactamente como se facilita.

## Paso 4: Agregar código de API de visitante a la página {#section-02d8dd7678b64a85b5abc1c4ef0845dd}

Implemente `VisitorAPI.js` el archivo en el sitio en `<head>` las etiquetas antes de la referencia al `mbox.js` archivo. El servicio [!DNL Experience Cloud] de ID debe ejecutarse antes de que se genere la primera [!DNL Target] llamada de red. Mueva este código a producción después de la prueba y verificación.

## Paso 5: Probar e implementar el código del servicio de ID {#section-e81ee439bb8a4c2abea43d76f3112e9c}

Puede probar e implementar de la siguiente manera.

**Probar y verificar**

Para probar la implementación de su servicio de ID:

* Compruebe la cookie AMCV en el dominio en el que está alojada su página.
* Compruebe `mboxMCGVID` que aparece en [!DNL Target] su solicitud y que contiene [!DNL Experience Cloud] el ID (MID).

Consulte [Cookies y el servicio Experience Cloud ID](../mcvid-introduction/mcvid-cookies.md) para obtener información sobre la cookie AMCV y el MID.

**Implementación**

Implementación del código una vez pasada la prueba.
