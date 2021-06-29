---
description: Se indican configuraciones del servidor de ejemplo y los pasos de migración necesarios.
keywords: Servicio de ID
title: Escenarios de migración del servicio de Experience Cloud ID
exl-id: 419532bf-399f-4646-a95f-31c35535d6fc
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: ht
source-wordcount: '380'
ht-degree: 100%

---

# Escenarios de migración del servicio de identidad de Experience Cloud {#experience-cloud-id-service-migration-scenarios}

Se indican configuraciones del servidor de ejemplo y los pasos de migración necesarios.

## Propiedad web única {#section-6ccfea84628d46c99507cb124e7f5445}

* **Cliente**: Empresa de Ejemplo S.A.
* **Experience Cloud habilitado**: No
* **Propiedades web**: ejemplo.com
* **Servidores de recopilación de datos**: metrics.ejemplo.com, smetrics.ejemplo.com
* **Archivo JavaScript de Analytics**: Un solo archivo para todas las páginas del sitio

En primer lugar, debe habilitarse Experience Cloud para este cliente (consulte los [requisitos](../../reference/requirements.md)). Y, como tienen un solo archivo JavaScript, este cliente no necesita ningún periodo de gracia. Este cliente también configurará la migración de visitantes y dejará de utilizar el CNAME de la recopilación de datos, que no es necesario.

## Varios archivos JavaScript, etiquetas de imagen predefinidas en el código {#section-a665f6ee202940449198e4e7a5dcac54}

* **Cliente**: Otra Empresa de Ejemplo S.A.
* **Experience Cloud habilitado**: Sí
* **Propiedades web**: otroejemplo.com
* **Servidores de recopilación de datos**: otroejemploco.112.2o7.net
* **Archivo JavaScript de Analytics**: Varios archivos JavaScript. Un archivo para su sitio principal y otro archivo para su sección de soporte, que se mantiene en un CMS independiente.
* **Otros métodos de recopilación de datos**: Etiquetas de imágenes predefinidas en una sección del sitio

En primer lugar, este cliente debe buscar su ID de organización de Adobe Experience Cloud (consulte los [requisitos](../../reference/requirements.md)). A continuación, deberá configurar un período de gracia de migración porque está utilizando varios archivos JavaScript. Este cliente también configurará la migración de visitantes y cambiará de `*.2o7.net` a `*.sc.omtrdc.net`.

Cuando este cliente actualice el código JavaScript de Analytics a la versión más reciente como preparación para la implementación del servicio de ID de [!DNL Experience Cloud], también actualizará todas las etiquetas de imagen predefinidas en el código para que utilicen JavaScript en su lugar.

## Varias propiedades web, varios archivos JavaScript y reproductor de vídeos basado en Flash {#section-34647995ff3740b999fdee22d885e515}

* **Cliente**: Buen Cliente S.A.
* **Experience Cloud habilitado**: Sí
* **Propiedades web**: misitioprincipal.com, miotrositioA.com, miotrositioB.com
* **Servidores de recopilación de datos**: metrics.misitioprincipal.com, smetrics.misitioprincipal.com
* **Archivo JavaScript de Analytics**: Varios archivos JavaScript. Un archivo por cada propiedad web.
* **Otros métodos de recopilación de datos**: Reproductor de vídeo basado en Flash

En primer lugar, este cliente debe buscar su ID de organización de Adobe Experience Cloud (consulte los [requisitos](../../reference/requirements.md)). A continuación, deberá configurar un período de gracia de migración porque está utilizando varios archivos JavaScript. Este cliente realiza un seguimiento de los visitantes entre su dominio principal y sus subdominios, de modo que seguirá utilizando el CNAME de recopilación de datos con el servicio de ID de visitantes.

Cuando este cliente actualice el código JavaScript de Analytics a la versión más reciente como preparación para la implementación del servicio de ID de [!DNL Experience Cloud], también actualizará el reproductor de vídeos basado en Flash a la última versión de AppMeasurement para Flash.
