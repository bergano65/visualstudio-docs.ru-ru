---
title: "Элемент UsedCommand | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Элемент UsedCommands (VSCT XML-схемы)"
  - "Элементы схемы VSCT XML, UsedCommands"
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Элемент UsedCommand
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Позволяет VSPackage для доступа к команде, которая определена в другом файле .vsct. Например, если VSPackage использует стандартную **копирования** команду, которая определяется [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] оболочки, можно добавить команду меню или панель инструментов без повторной реализации.  
  
## Синтаксис  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|Идентификатор GUID|Обязательный. Идентификатор GUID пары идентификатор GUID, который определяет команду.|  
|id|Обязательный. Идентификатор пары идентификатор GUID, который определяет команду.|  
|Условие|Необязательный. См. раздел [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|Нет||  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Элемент UsedCommands](../extensibility/usedcommands-element.md)|Группирует элементы UsedCommand и других UsedCommands группирований.|  
  
## Заметки  
 Путем добавления команды `<UsedCommands>` элемента, сообщает VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] среды, что VSPackage необходима команда. Следует добавить `<UsedCommand>` элемент для любой команды пакета требует, не могут быть включены во всех версиях и конфигурации Visual Studio. Например, если пакет вызывает команду, которая относится к Visual C\+\+, команда не будет доступна пользователям Visual Web Developer Если включить `<UsedCommand>` элемент для команды.  
  
## Пример  
  
```  
<UsedCommands> <UsedCommand guid="guidVSStd97" id="cmdidCut"/> <UsedCommand guid="guidVSStd97" id="cmdidCopy"/> <UsedCommand guid="guidVSStd97" id="cmdidPaste"/> </UsedCommands>  
```  
  
## См. также  
 [Элемент UsedCommands](../extensibility/usedcommands-element.md)   
 [Таблицы команд Visual Studio \(. Файлы Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)