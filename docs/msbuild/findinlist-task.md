---
title: "Задача FindInList | Microsoft Docs"
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
  - "FindInList - задача [MSBuild]"
  - "MSBuild, FindInList - задача"
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача FindInList
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ищет в заданном списке элемент, имеющий указанную спецификацию.  
  
## Параметры  
 В следующей таблице описаны параметры задачи [FindInList Task](../msbuild/findinlist-task.md).  
  
|Параметр|Описание|  
|--------------|--------------|  
|`CaseSensitive`|Необязательный параметр типа `Boolean`.<br /><br /> Если этот параметр равен `true`, поиск чувствителен к регистру символов, в противном случае регистр не имеет значения.  Значение по умолчанию — `true`.|  
|`FindLastMatch`|Необязательный параметр типа `Boolean`.<br /><br /> Если этот параметр равен `true`, возвращается последнее совпадение; в противном случае возвращается первое совпадение.  Значение по умолчанию — `false`.|  
|`ItemFound`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`, предназначенный только для чтения.<br /><br /> В списке находится первый совпадающий элемент, если таковой имеется.|  
|`ItemSpecToFind`|Обязательный параметр типа `String`.<br /><br /> Искомая спецификация элемента.|  
|`List`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Список, в котором нужно выполнить поиск спецификации элемента.|  
|`MatchFileNameOnly`|Необязательный параметр типа `Boolean`.<br /><br /> Если этот параметр равен `true`, сравнение производится только с той частью спецификации элемента, которая содержит имя файла; в противном случае сравнение производится со всей спецификацией элемента.  Значение по умолчанию — `true`.|  
  
## Заметки  
 Помимо параметров, которые перечислены выше, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследует от класса <xref:Microsoft.Build.Utilities.Task>.  Чтобы получить список этих доп параметров и их описаний, см. [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)