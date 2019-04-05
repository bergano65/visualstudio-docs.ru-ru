---
title: Элемент LocalizedName (схема языкового пакета VSIX) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 57b7f502-3b04-42d9-90d5-f57772a7c757
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0747dfe89c2d8d4ceb8321f00f723f973f3ff526
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991732"
---
# <a name="localizedname-element-vsix-language-pack-schema"></a>Элемент LocalizedName (схема языкового пакета VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Обязательный. Локализованное имя расширения должны быть установлены.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Name>Localized name of the extension</Name>  
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
 Обязательный. Имя языкового пакета на целевом языке.  
  
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
