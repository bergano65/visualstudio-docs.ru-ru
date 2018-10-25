---
title: Структура файл [Content_types] .xml | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 538a518d1186dc50a9e5e89635af0a07c2542041
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893277"
---
# <a name="the-structure-of-the-contenttypesxml-file"></a>Структура файла [типы_содержимого].xml
Содержит сведения о типах содержимого в пакете VSIX. Visual Studio использует файл [Content_Types] .xml для установки пакета, но не устанавливает сам файл.  
  
> [!NOTE]
>  Несмотря на то, что этот раздел относится только к [Content_Type] XML-файлы, которые используются в пакетах VSIX, тип файла [Content_Types] .xml является частью *Open Packaging Conventions (OPC)* standard. Дополнительные сведения см. в разделе [OPC: новый стандартный для упаковки данных](http://go.microsoft.com/fwlink/?LinkID=148207) на сайте MSDN.  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах корневого элемента и его атрибуты и дочерние элементы.  
  
### <a name="root-element"></a>Корневой элемент  
  
|Элемент|Описание|  
|-------------|-----------------|  
|`Types`|Содержит дочерние элементы, соответствующие типам файлов в пакете VSIX.|  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Xmlns`|(Обязательно). Расположение схемы, используемой для этого файл [Content_Types] .xml.|  
  
### <a name="attribute-name-attribute"></a>{Атрибут name} Атрибут  
  
| Значение | Описание |
| - | - |
| http://schemas.openformats.org/package/2006/content-types | Расположение схемы типов содержимого. |
  
### <a name="child-elements"></a>Дочерние элементы  
 `Types` Элемент может содержать любое количество `Default` элементов.  
  
|Элемент|Описание|  
|-------------|-----------------|  
|`Default`|Описывает тип содержимого в пакете VSIX. Каждый тип файла в пакете должно иметь свой собственный `Default` элемент.|  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Extension`|Расширение имени файла, файла в пакете VSIX.|  
|`ContentType`|Описывает тип содержимого, связанного с расширением имени файла.|  
  
### <a name="attribute-name-attribute"></a>{Атрибут name} Атрибут  
 Visual Studio распознает следующие `ContentType` значения для связанного `Extension` типов.  
  
|Расширение|ContentType|  
|---------------|-----------------|  
|txt|text/plain|  
|pkgdef|text/plain|  
|xml|text/xml|  
|VSIXMANIFEST|text/xml|  
|htm или html|text/html|  
|RTF|приложение или rtf|  
|PDF-файл|Application/pdf|  
|GIF|изображение/gif|  
|JPG или jpeg|изображение или jpg|  
|TIFF|изображение/tiff|  
|vsix|Application/zip|  
|ZIP|Application/zip|  
|dll|application/octet-stream|  
|все другие типы файлов|application/octet-stream|  
  
## <a name="example"></a>Пример  
  
### <a name="description"></a>Описание  
 Следующий файл [Content_Types] .xml описывает типичные пакета VSIX.  
  
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
 [Составляющие пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Справочник по схеме 1.0 расширение VSIX](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: Новый стандарт упаковки данных](http://go.microsoft.com/fwlink/?LinkID=148207)