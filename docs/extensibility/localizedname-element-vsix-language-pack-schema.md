---
title: "Элемент LocalizedName (схема языкового пакета VSIX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57b7f502-3b04-42d9-90d5-f57772a7c757
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Элемент LocalizedName (схема языкового пакета VSIX)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Обязательный. Локализованное имя расширения должны быть установлены.  
  
## Синтаксис  
  
```  
<Name>Localized name of the extension</Name>  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|Нет||  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|Нет||  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Элемент LanguagePack VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Обязательный. Предоставляет корневой элемент для языкового пакета VSIX.|  
  
## Текстовое значение  
 Обязательный. Имя языкового пакета на целевом языке.  
  
## Сведения об элементе  
  
|||  
|-|-|  
|Пространство имен|http:\/\/schemas.Microsoft.com\/Developer\/VSX\-Schema\-LP\/2010|  
|Имя схемы|Схема языкового пакета VSIX|  
|Файл проверки|VSIXLanguagePackSchema.xsd|  
|Может быть пустым|Неприменимо|  
  
## См. также  
 [Справочник по схеме пакета языка VSX](../extensibility/vsx-language-pack-schema-reference.md)   
 [Локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md)   
 [Справочник по схеме 1.0 расширения VSIX](http://msdn.microsoft.com/ru-ru/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)