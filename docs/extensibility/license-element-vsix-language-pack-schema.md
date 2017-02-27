---
title: "Элемент License (схема языкового пакета VSIX) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57dac3b7-0cdd-405c-9af5-30ed9ca45e53
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Элемент License (схема языкового пакета VSIX)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Необязательный. Путь к локализованной версии файла лицензии расширения.  
  
## Синтаксис  
  
```  
<License>FilePath\license.txt</License>  
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
 Относительный путь к локализованному файлу лицензии для отображения.  
  
## Заметки  
 Если `License` определяется элемент, а затем во время установки отображается текст назначенного файла лицензии, и пользователь должен принять лицензию для продолжения.  
  
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