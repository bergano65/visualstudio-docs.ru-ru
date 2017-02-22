---
title: "Элемент GuidSymbol | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Элементы схемы VSCT XML, GuidSymbol"
  - "Элемент GuidSymbol (VSCT XML-схемы)"
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Элемент GuidSymbol
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`GuidSymbol` Элемент содержит идентификатор GUID GUID:ID пары, который представляет меню, группы или команды. Идентификатор поступает из `IDSymbol` элемент в `GuidSymbol` элемент.`GuidSymbol` Элемент имеет `name` атрибут, предоставляющий понятное имя для идентификатора GUID, который содержится в `value` атрибута.  
  
## Синтаксис  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|имя|Обязательный. Имя символа идентификатора GUID.|  
|значение|Обязательный. Идентификатор GUID символом GUID.|  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Элемент IDSymbol](../extensibility/idsymbol-element.md)|Содержит идентификатор GUID:ID пары, который представляет меню, группы или команды.|  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Элемент символы](../extensibility/symbols-element.md)|Группы `GuidSymbol` элементы в файле .vsct.|  
  
## Заметки  
 Как правило, файл .vsct содержит три `GuidSymbol` элементов в его `Symbols` статьи, один для самого пакета, один для набора команд \(коллекция меню, групп и команд, которые делает доступными пакета\) и один для точечных рисунков, которые предоставляют значки для кнопок и другие визуальные компоненты. Каждый `IDSymbol` элемент в заданной `GuidSymbol` элемент должен иметь уникальный `value`. Тем не менее `IDSymbol` элементы, имеющие одинаковые значения могут существовать в пакет, пока они имеют разные родительские элементы.  
  
## См. также  
 [Таблицы команд Visual Studio \(. Файлы Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)