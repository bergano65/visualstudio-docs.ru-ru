---
title: Базовый класс Task | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 6c3f6238-b9f0-4325-b8b0-de61090bd0a2
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b2b269d718871c58cb082ce09ed50ce70736b55
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562592"
---
# <a name="task-base-class"></a>Базовый класс Task
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [базовый класс Task](https://docs.microsoft.com/visualstudio/msbuild/task-base-class).  
  
  
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



