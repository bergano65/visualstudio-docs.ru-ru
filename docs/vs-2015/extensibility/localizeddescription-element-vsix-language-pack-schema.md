---
title: Элемент LocalizedDescription (схема языкового пакета VSIX) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 766a1732-bbaf-4875-b276-feb42169633a
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9e626e532c462199d38ddb3f1044bab25d389995
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58980325"
---
# <a name="localizeddescription-element-vsix-language-pack-schema"></a>Элемент LocalizedDescription (схема языкового пакета VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Обязательный. Локализованное описание расширения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<LocalizedDescription>Localized description of the extension</LocalizedDescription>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|Нет||  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|Нет||  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент LanguagePack VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Обязательный. Предоставляет корневой элемент для языкового пакета VSIX.|  
  
## <a name="text-value"></a>Текстовое значение  
 Обязательный. Текстовое описание расширения на целевом языке.  
  
## <a name="element-information"></a>Сведения об элементе  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Пространство имен    | http://schemas.microsoft.com/developer/vsx-schema-lp/2010 |
|   Имя схемы   |                 Схема языкового пакета VSIX                 |
| Файл проверки |                VSIXLanguagePackSchema.xsd                 |
|  Может быть пустым   |                      Неприменимо                       |
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме VSX языкового пакета](../extensibility/vsx-language-pack-schema-reference.md)   
 [Локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md)   
 [Справочник по схеме 1.0 расширение VSIX](http://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
