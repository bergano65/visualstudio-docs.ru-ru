---
title: "Элемент VSIXLanguagePack (схема языкового пакета VSIX) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Элемент VSIXLanguagePack (схема языкового пакета VSIX)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Обязательный. Предоставляет корневой элемент для языкового пакета VSIX. Языковой пакет VSIX предоставляет локализованные сведения об установке для пакета VSIX.  
  
## Синтаксис  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`xmlns`|Пространство имен XML, в котором определена схема языкового пакета VSIX.|  
  
## Атрибут xmlns  
  
|Значение|Описание|  
|--------------|--------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|Обязательный. Расположение файла, который определяет схему для языковых пакетов.|  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Элемент LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md)|Обязательный. Локализованное имя расширения должны быть установлены.|  
|[Элемент LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|Обязательный. Локализованное описание расширения должны быть установлены.|  
|[Элемент MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|Необязательный. Ссылка на локализованные сведения о расширении.|  
|[Элемент лицензии](../extensibility/license-element-vsix-language-pack-schema.md)|Необязательный. Путь к локализованной версии файла лицензии расширения.|  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|Нет||  
  
## Сведения об элементе  
  
|||  
|-|-|  
|Пространство имен|http:\/\/schemas.Microsoft.com\/Developer\/VSX\-Schema\-LP\/2010|  
|Имя схемы|Схема языкового пакета VSIX|  
|Файл проверки|VSIXLanguagePackSchema.xsd|  
|Может быть пустым|Нет|  
  
## См. также  
 [Справочник по схеме пакета языка VSX](../extensibility/vsx-language-pack-schema-reference.md)   
 [Локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md)   
 [Справочник по схеме 1.0 расширения VSIX](http://msdn.microsoft.com/ru-ru/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)