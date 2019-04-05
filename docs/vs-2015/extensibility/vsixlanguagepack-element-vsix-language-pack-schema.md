---
title: Элемент VSIXLanguagePack (схема языкового пакета VSIX) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7b4ba4e98b8b2d42485a7594d5bab658e1bd6ccb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992097"
---
# <a name="vsixlanguagepack-element-vsix-language-pack-schema"></a>Элемент VSIXLanguagePack (схема языкового пакета VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Обязательный. Предоставляет корневой элемент для языкового пакета VSIX. Языковой пакет VSIX предоставляет локализованные сведения об установке для пакета VSIX.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`xmlns`|Пространство имен XML, в котором определяется схема языкового пакета VSIX.|  
  
## <a name="xmlns-attribute"></a>Атрибут xmlns  
  
|Значение|Описание|  
|-----------|-----------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|Обязательный. Расположение файла, который определяет схему для языковых пакетов.|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md)|Обязательный. Локализованное имя расширения должны быть установлены.|  
|[Элемент LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|Обязательный. Локализованное описание расширения должны быть установлены.|  
|[Элемент MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|Необязательный параметр. Ссылка на локализованную информацию о расширении.|  
|[Элемент License](../extensibility/license-element-vsix-language-pack-schema.md)|Необязательный параметр. Путь к локализованной версии файла лицензии для расширения.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|Нет||  
  
## <a name="element-information"></a>Сведения об элементе  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Пространство имен    | http://schemas.microsoft.com/developer/vsx-schema-lp/2010 |
|   Имя схемы   |                 Схема языкового пакета VSIX                 |
| Файл проверки |                VSIXLanguagePackSchema.xsd                 |
|  Может быть пустым   |                            Нет                             |
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме VSX языкового пакета](../extensibility/vsx-language-pack-schema-reference.md)   
 [Локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md)   
 [Справочник по схеме 1.0 расширение VSIX](http://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
