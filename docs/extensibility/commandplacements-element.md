---
title: "Элемент CommandPlacements | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CommandPlacements"
helpviewer_keywords: 
  - "Элемент CommandPlacements (VSCT XML-схемы)"
  - "Элементы схемы VSCT XML, CommandPlacements"
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Элемент CommandPlacements
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Элемент CommandPlacements группы элементов CommandPlacement и других CommandPlacements группирований.  
  
 CommandPlacements элемент является необязательным. Если нет, группы или меню необходимо включить в дополнительном расположении, не нужно включать этот раздел в файл .vsct.  
  
## Синтаксис  
  
```  
<CommandPlacements>  
  <CommandPlacement>... </CommandPlacement>  
  <CommandPlacement>... </CommandPlacement>  
</CommandPlacements>  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|Условие|Необязательный. См. раздел [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|CommandPlacements|Группирует элементы CommandPlacement и других CommandPlacements группирований.|  
|[Элемент CommandPlacement](../extensibility/commandplacement-element.md)|Включает кнопки, группы и меню, должны быть включены в более чем одной группе или меню.|  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, представляющие команды.|  
  
## Пример  
  
```  
<CommandPlacements> <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions" priority="0x0300"> <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/> </CommandPlacement> </CommandPlacements>  
```  
  
## См. также  
 [Элемент CommandPlacement](../extensibility/commandplacement-element.md)   
 [Таблицы команд Visual Studio \(. Файлы Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)