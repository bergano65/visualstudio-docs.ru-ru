---
title: "Элемент IDSymbol | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Элемент IDSymbol (VSCT XML-схемы)"
  - "Элементы схемы VSCT XML, IDSymbol"
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Элемент IDSymbol
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`IDSymbol` Элемент содержит идентификатор GUID:ID пары, который представляет меню, группы или команды. Идентификатор GUID поступает из родительского `GuidSymbol` элемента.`IDSymbol` Элемент имеет `name` атрибут, предоставляющий понятное имя для идентификатора, который содержится в `value` атрибута.  
  
## Синтаксис  
  
```  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|имя|Обязательный. Имя символа идентификатора.|  
|значение|Обязательный. Числовое значение идентификатора символ идентификатора.|  
  
### Дочерние элементы  
 Отсутствует.  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Элемент GuidSymbol](../extensibility/guidsymbol-element.md)|Содержит идентификатор GUID GUID:ID пары, который представляет меню, группы или команды. Группирует элементы `IDSymbol`.|  
  
## Заметки  
 Каждый `IDSymbol` элемент в заданной `GuidSymbol` элемент должен иметь уникальный `value`. Тем не менее `IDSymbol` элементы, имеющие одинаковые значения могут существовать в пакет, пока они имеют разные родительские элементы.  
  
## См. также  
 [Таблицы команд Visual Studio \(. Файлы Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)