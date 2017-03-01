---
title: "Структура XML-файла [Content_types] | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 7278fb37984b92a6a07823c552db5c59a446d0d2
ms.openlocfilehash: 6f45707a88a27fa54840825d9562f859385ce4b7
ms.lasthandoff: 02/22/2017

---
# <a name="the-structure-of-the-contenttypesxml-file"></a>Структура файл [Content_types] .xml
Содержит сведения о типах содержимого в пакете VSIX. Visual Studio использует файл [Content_Types] .xml для установки пакета, но сам файл не устанавливаются.  
  
> [!NOTE]
>  Несмотря на то, что этот раздел относится только к [Content_Type] XML-файлов, используемых в пакетах VSIX, тип файла [Content_Types] .xml является частью *Open Packaging Conventions (OPC)* standard. Дополнительные сведения см. в разделе [OPC: новый стандартный для упаковки данных](http://go.microsoft.com/fwlink/?LinkID=148207) на веб-сайте MSDN.  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны корневой элемент и его атрибуты и дочерние элементы.  
  
### <a name="root-element"></a>Корневой элемент  
  
|Элемент|Описание|  
|-------------|-----------------|  
|`Types`|Содержит дочерние элементы, соответствующие типам файлов в пакете VSIX.|  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Xmlns`|(Обязательно). Расположение схемы, используемой для этого файл [Content_Types] .xml.|  
  
### <a name="attribute-name-attribute"></a>{Имя_атрибута} Атрибут  
  
|Значение|Описание|  
|-----------|-----------------|  
|http://schemas.openformats.org/Package/2006/Content-Types|Расположение схемы типов содержимого.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 `Types` Элемент может содержать любое количество `Default` элементы.  
  
|Элемент|Описание|  
|-------------|-----------------|  
|`Default`|Описывает тип содержимого в пакете VSIX. Каждому типу файла в пакете должен иметь свой собственный `Default` элемента.|  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Extension`|Расширение имени файла в пакете VSIX.|  
|`ContentType`|Описывает тип содержимого, связанного с расширением имени файла.|  
  
### <a name="attribute-name-attribute"></a>{Имя_атрибута} Атрибут  
 Visual Studio распознает следующие `ContentType` значения для связанного `Extension` типов.  
  
|Расширение|Тип содержимого|  
|---------------|-----------------|  
|txt|text/plain.|  
|pkgdef|text/plain.|  
|xml|text/xml|  
|VSIXMANIFEST|text/xml|  
|htm или html|текст или html|  
|RTF|приложения, rtf|  
|PDF|Application/pdf|  
|GIF|изображение или gif|  
|JPG или jpeg|изображение или jpg|  
|TIFF|изображение или tiff|  
|vsix|приложение или zip|  
|ZIP|приложение или zip|  
|dll|приложения/octet-stream|  
|все другие типы файлов|приложения/octet-stream|  
  
## <a name="example"></a>Пример  
  
### <a name="description"></a>Описание  
 Следующий файл [Content_Types] .xml описывает типичный пакет VSIX.  
  
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
 [Справочник по схеме 1.0 расширения VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: Новый стандарт упаковки данных](http://go.microsoft.com/fwlink/?LinkID=148207)
