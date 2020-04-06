---
title: Структура файла «Content_types.xml» Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2761e012d32516265e61c8001491e3c605372ff5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699025"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Структура файла [типы_содержимого].xml
Содержит информацию о видах содержимого в пакете VSIX. Visual Studio использует файл «Content_Types.xml для установки пакета, но сам файл не устанавливается.

> [!NOTE]
> Хотя эта тема применима только к файлам «Content_Type.xml, которые используются в пакетах VSIX, тип файла «Content_Types». *Open Packaging Conventions (OPC)* Для получения дополнительной информации [см.](https://msdn.microsoft.com/magazine/cc163372.aspx)

## <a name="attributes-and-elements"></a>Атрибуты и элементы
 В следующих разделах описаны корневой элемент, его атрибуты и элементы ребенка.

### <a name="root-element"></a>Корневой элемент

|Элемент|Описание|
|-------------|-----------------|
|`Types`|Содержит элементы ребенка, перечисляющие типы файлов в пакете VSIX.|

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`Xmlns`|(Обязательно.) Расположение схемы, используемой для этого файла «Content_Types.xml.|

### <a name="attribute-name-attribute"></a>(Имя атрибута) Атрибут

| Значение | Описание |
| - | - |
| `http://schemas.openformats.org/package/2006/content-types` | Расположение схемы типов содержимого. |

### <a name="child-elements"></a>Дочерние элементы
 Элемент `Types` может содержать любое число элементов `Default`.

|Элемент|Описание|
|-------------|-----------------|
|`Default`|Описывает тип содержимого в пакете VSIX. Каждый тип файла в `Default` пакете должен иметь свой собственный элемент.|

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`Extension`|Расширение файла в пакете VSIX.|
|`ContentType`|Описывает вид содержимого, связанного с расширением имени файла.|

### <a name="attribute-name-attribute"></a>(Имя атрибута) Атрибут
 Visual Studio распознает `ContentType` следующие значения `Extension` для связанных типов.

|Расширение|ContentType|
|---------------|-----------------|
|txt|text/plain|
|pkgdef|text/plain|
|Xml|text/xml|
|vsixmanifest|text/xml|
|htm или html|text/html|
|Rtf|приложение/rtf|
|pdf|приложение/pdf|
|GIF|image/gif|
|jpg или jpeg|изображение/jpg|
|tiff|image/tiff|
|vsix|применение/zip|
|zip|применение/zip|
|Файл DLL.|application/octet-stream|
|все другие типы файлов|application/octet-stream|

## <a name="example"></a>Пример

### <a name="description"></a>Описание
 Следующий файл «Content_Types.xml описывает типичный пакет VSIX.

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
- [Схема расширения VSIX 1.0 Справка](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [OPC: новый стандарт для упаковки данных](https://msdn.microsoft.com/magazine/cc163372.aspx)
