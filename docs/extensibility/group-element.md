---
title: "Элемент группы | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Элементы схемы VSCT XML, групп"
  - "Элемент Groups (VSCT XML-схемы)"
ms.assetid: 69faee18-cbf4-470a-b952-c1919c583df8
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Элемент группы
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Определяет группу команды VSPackage.  
  
## Синтаксис  
  
```  
<Group guid="guidMyCommandSet" id="MyGroup" priority="0x101">  
  <Parent>... </Parent>  
</Group>  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|Идентификатор GUID|Обязательный. Идентификатор GUID идентификатор GUID и идентификатор команды.|  
|id|Обязательный. Идентификатор идентификатор GUID и идентификатор команды.|  
|priority|Необязательный. Числовое значение, указывающее приоритет.|  
|Условие|Необязательный. См. раздел [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|Родительский|Необязательный. Родительский элемент кнопки.|  
|Комментарий|Необязательный комментарий.|  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Элемент Groups](../extensibility/groups-element.md)|Содержит элементы, которые определяют группы команды VSPackage.|  
  
## Пример  
  
```  
<Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"> <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/> </Group>  
```  
  
## См. также  
 [Таблицы команд Visual Studio \(. Файлы Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)