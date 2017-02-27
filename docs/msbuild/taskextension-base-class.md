---
title: "Базовый класс TaskExtension | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "MSBuild, tool task - базовый класс"
  - "tool task - базовый класс [MSBuild]"
ms.assetid: 08bb8059-b7e2-4565-89ba-d9034d4f0e16
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# Базовый класс TaskExtension
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Многие задачи наследуются от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который наследуется от класса <xref:Microsoft.Build.Utilities.Task>.  Эта цепочка наследований добавляет несколько параметров для задач, которые являются производными от них.  Эти параметры перечислены в настоящем документе.  
  
## Параметры  
 В следующей таблице описаны параметры базовый классов.  
  
|Параметр|Описание|  
|--------------|--------------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Необязательный параметр типа <xref:Microsoft.Build.Framework.IBuildEngine>.<br /><br /> Задает имя интерфейса подсистемы построения, который доступен для задач.  Подсистема построения автоматически устанавливает этот параметр, чтобы разрешить задачам обратный вызов.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Необязательный параметр типа <xref:Microsoft.Build.Framework.IBuildEngine2>.<br /><br /> Задает имя интерфейса подсистемы построения, который доступен для задач.  Подсистема построения автоматически устанавливает этот параметр, чтобы разрешить задачам обратный вызов.<br /><br /> Это удобное свойство; значение авторов задачи, унаследованное от этого класса, не должно быть приведено из `IBuildEngine` к `IBuildEngine2`.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Необязательный параметр типа <xref:Microsoft.Build.Framework.IBuildEngine3>.<br /><br /> Указывает интерфейс обработчика построения, предоставляемый хостом.|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Необязательный параметр типа <xref:Microsoft.Build.Framework.ITaskHost>.<br /><br /> Указывает экземпляр объекта сайта \(может быть пустым\).  Подсистема построения задает это свойство, если с данной задачей связан объект узла в интегрированной среде разработки \(IDE\) узла.|  
|<xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>|Необязательный параметр <xref:Microsoft.Build.Utilities.TaskLoggingHelper>, предназначенный только для чтения.<br /><br /> Получает объект `TaskLoggingHelperExtension`, содержащий методы ведения журналов для задачи.|  
  
## См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Задачи](../msbuild/msbuild-tasks.md)