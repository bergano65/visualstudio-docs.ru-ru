---
title: Базовый класс Task | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 6c3f6238-b9f0-4325-b8b0-de61090bd0a2
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2b1d82356d2f19388fd642214d03c1a1097b81ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149458"
---
# <a name="task-base-class"></a>Базовый класс Task
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В конечном счете многие задачи наследуются от класса <xref:Microsoft.Build.Utilities.Task>. Этот класс добавляет несколько параметров в задачи, производные от него. Эти параметры перечислены в настоящем документе.  
  
## <a name="parameters"></a>Параметры  
 Приведенная ниже таблица описывает параметры этого базового класса.  
  
|Параметр|Description|  
|---------------|-----------------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Необязательный параметр <xref:Microsoft.Build.Framework.IBuildEngine>.<br /><br /> Задает интерфейс подсистемы сборки, доступный для задач. Подсистема сборки автоматически устанавливает этот параметр, чтобы разрешить задачам обратный вызов.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Необязательный параметр <xref:Microsoft.Build.Framework.IBuildEngine2>.<br /><br /> Задает интерфейс подсистемы сборки, доступный для задач. Подсистема сборки автоматически устанавливает этот параметр, чтобы разрешить задачам обратный вызов.<br /><br /> Это свойство предусмотрено для удобства, чтобы разработчикам, наследующим из этого класса, не приходилось приводить значение из `IBuildEngine` в `IBuildEngine2`.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Необязательный параметр <xref:Microsoft.Build.Framework.IBuildEngine3>.<br /><br /> Задает интерфейс подсистемы сборки, предоставляемый узлом.|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskHost>.<br /><br /> Указывает экземпляр объекта узла (может иметь значение null). Подсистема сборки задает это свойство, если интегрированная среда разработки узла связывает объект узла с этой конкретной задачей.|  
|<xref:Microsoft.Build.Utilities.Task.Log%2A>|Необязательный параметр <xref:Microsoft.Build.Utilities.TaskLoggingHelper>, доступный только для чтения.<br /><br /> Вспомогательный объект ведения журнала.|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по задачам](../msbuild/msbuild-task-reference.md)   
 [Задачи](../msbuild/msbuild-tasks.md)
