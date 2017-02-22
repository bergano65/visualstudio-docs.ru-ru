---
title: "Задача Move | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Move - задача [MSBuild]"
  - "MSBuild, Move - задача"
ms.assetid: d1405347-1309-4f18-b565-905408093d59
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача Move
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Перемещение файлов в новое расположение.  
  
## Параметры  
 В следующей таблице описаны параметры задачи `Move`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`DestinationFiles`|Необязательный выходной параметр типа <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Этот параметр указывает список, в который будут перемещены исходные файлы.  Предполагается, что этот список будет взаимно\-однозначно сопоставляться со списком, заданным параметром `SourceFiles`.  То есть первый файл из списка `SourceFiles` будет перемещен с использованием первого пути, заданного в списке `DestinationFiles`, и т. д.|  
|`DestinationFolder`|Необязательный параметр типа <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> указывает каталог, в который требуется переместить файлы.|  
|`MovedFiles`|Необязательный выходной параметр типа <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Этот параметр содержит успешно перемещенные элементы.|  
|`OverwriteReadOnlyFiles`|Необязательный параметр типа `Boolean`.<br /><br /> Если значение `true`, перезаписываются даже файлы, доступные только для чтения.|  
|`SourceFiles`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Указывает файлы для перемещения.|  
  
## Заметки  
 Может быть указан либо параметр `DestinationFolder`, либо `DestinationFiles`, но не оба одновременно.  Если указаны оба параметра, задача прерывает работу и в журнале событий регистрируется ошибка.  
  
 В дополнение к параметры, которые перечислены в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса<xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)