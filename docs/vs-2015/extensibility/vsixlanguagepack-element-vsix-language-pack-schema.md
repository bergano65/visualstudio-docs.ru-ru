---
title: Элемент VSIXLanguagePack (схема языкового пакета VSIX) | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8cc63f24f50f8ed0fecb9640ae4b2a5d2ec669be
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49224748"
---
# <a name="vsixlanguagepack-element-vsix-language-pack-schema"></a>Элемент VSIXLanguagePack (схема языкового пакета VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Обязательно. Предоставляет корневой элемент для языкового пакета VSIX. Языковой пакет VSIX предоставляет локализованные сведения об установке для пакета VSIX.  
  
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
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|Обязательно. Расположение файла, который определяет схему для языковых пакетов.|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md)|Обязательно. Локализованное имя расширения должны быть установлены.|  
|[Элемент LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|Обязательно. Локализованное описание расширения должны быть установлены.|  
|[Элемент MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|Необязательный. Ссылка на локализованную информацию о расширении.|  
|[Элемент License](../extensibility/license-element-vsix-language-pack-schema.md)|Необязательный. Путь к локализованной версии файла лицензии для расширения.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|Нет||  
  
## <a name="element-information"></a>Сведения об элементе  
  
|||  
|-|-|  
|Пространство имен|http://schemas.microsoft.com/developer/vsx-schema-lp/2010|  
|Имя схемы|Схема языкового пакета VSIX|  
|Файл проверки|VSIXLanguagePackSchema.xsd|  
|Может быть пустым|Нет|  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме VSX языкового пакета](../extensibility/vsx-language-pack-schema-reference.md)   
 [Локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md)   
 [Справочник по схеме 1.0 расширение VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)

