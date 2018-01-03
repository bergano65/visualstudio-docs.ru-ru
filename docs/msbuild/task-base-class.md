---
title: "Базовый класс Task | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 6c3f6238-b9f0-4325-b8b0-de61090bd0a2
caps.latest.revision: "6"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f3baa0185a917f5c89142f97668b08999e0f4f2f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="task-base-class"></a>Базовый класс Task
В конечном счете многие задачи наследуются от класса <xref:Microsoft.Build.Utilities.Task>. Этот класс добавляет несколько параметров в задачи, производные от него. Эти параметры перечислены в настоящем документе.  
  
## <a name="parameters"></a>Параметры  
 Приведенная ниже таблица описывает параметры этого базового класса.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Необязательный параметр <xref:Microsoft.Build.Framework.IBuildEngine> .<br /><br /> Задает интерфейс подсистемы сборки, доступный для задач. Подсистема сборки автоматически устанавливает этот параметр, чтобы разрешить задачам обратный вызов.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Необязательный параметр <xref:Microsoft.Build.Framework.IBuildEngine2> .<br /><br /> Задает интерфейс подсистемы сборки, доступный для задач. Подсистема сборки автоматически устанавливает этот параметр, чтобы разрешить задачам обратный вызов.<br /><br /> Это свойство предусмотрено для удобства, чтобы разработчикам, наследующим из этого класса, не приходилось приводить значение из `IBuildEngine` в `IBuildEngine2`.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Необязательный параметр <xref:Microsoft.Build.Framework.IBuildEngine3> .<br /><br /> Задает интерфейс подсистемы сборки, предоставляемый узлом.|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskHost> .<br /><br /> Указывает экземпляр объекта узла (может иметь значение null). Подсистема сборки задает это свойство, если интегрированная среда разработки узла связывает объект узла с этой конкретной задачей.|  
|<xref:Microsoft.Build.Utilities.Task.Log%2A>|Необязательный параметр <xref:Microsoft.Build.Utilities.TaskLoggingHelper>, доступный только для чтения.<br /><br /> Вспомогательный объект ведения журнала.|  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Задачи](../msbuild/msbuild-tasks.md)