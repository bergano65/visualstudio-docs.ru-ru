---
title: Структура файла [Content_types]. XML | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5cc42a5346498c04f759956b2ca00094ac1df119
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718729"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Структура файла [типы_содержимого].xml
Содержит сведения о типах содержимого в пакете VSIX. Visual Studio использует файл [Content_Types]. XML для установки пакета, но не устанавливает сам файл.

> [!NOTE]
> Хотя этот раздел применим только к файлам [Content_Type]. XML, которые используются в пакетах VSIX, тип файла [Content_Types]. XML является частью стандарта *Open Packaging Conventions (OPC)* . Дополнительные сведения см. в статье [OPC: новый стандарт для упаковки данных](http://go.microsoft.com/fwlink/?LinkID=148207) на веб-сайте MSDN.

## <a name="attributes-and-elements"></a>Атрибуты и элементы
 В следующих разделах описывается корневой элемент, его атрибуты и дочерние элементы.

### <a name="root-element"></a>Корневой элемент

|Элемент|Описание|
|-------------|-----------------|
|`Types`|Содержит дочерние элементы, которые перечисляют типы файлов в пакете VSIX.|

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`Xmlns`|(Обязательно.) Расположение схемы, используемой для этого файла [Content_Types]. XML.|

### <a name="attribute-name-attribute"></a>{Имя атрибута} Версию

| значения | Описание |
| - | - |
| http://schemas.openformats.org/package/2006/content-types | Расположение схемы типов содержимого. |

### <a name="child-elements"></a>Дочерние элементы
 Элемент `Types` может содержать любое количество элементов `Default`.

|Элемент|Описание|
|-------------|-----------------|
|`Default`|Описывает тип содержимого в пакете VSIX. Каждый тип файлов в пакете должен иметь собственный элемент `Default`.|

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`Extension`|Расширение имени файла в пакете VSIX.|
|`ContentType`|Описывает тип содержимого, связанного с расширением имени файла.|

### <a name="attribute-name-attribute"></a>{Имя атрибута} Версию
 Visual Studio распознает следующие `ContentType` значения для связанных типов `Extension`.

|Расширение|contentType|
|---------------|-----------------|
|текстовые|text/plain|
|pkgdef|text/plain|
|xml|text/xml|
|vsixmanifest|text/xml|
|htm или HTML|Text/HTML|
|RTF|приложение/RTF|
|файлов|приложение/PDF|
|файл|изображение/GIF|
|JPG или JPEG|Image/JPG|
|-|изображение/TIFF|
|vsix|приложение/ZIP-файл|
|zip|приложение/ZIP-файл|
|dll|application/octet-stream|
|Все прочие типы файлов|application/octet-stream|

## <a name="example"></a>Пример

### <a name="description"></a>Описание
 Следующий файл [Content_Types]. XML описывает типичный пакет VSIX.

### <a name="code"></a>Код

```
<?xml version="1.0" encoding="utf-8" ?>
<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">
    <Default Extension="vsixmanifest" ContentType="text/xml" />
    <Default Extension="dll" ContentType="application/octet-stream" />
    <Default Extension="png" ContentType="application/octet-stream" />
    <Default Extension="txt" ContentType="text/plain" />
    <Default Extension="pkgdef" ContentType="text/plain" />
</Types>
```

## <a name="see-also"></a>См. также
- [Составляющие пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Справочник по схеме расширения VSIX 1,0](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [OPC: новый стандарт для упаковки данных](http://go.microsoft.com/fwlink/?LinkID=148207)