---
title: Метод Жетсчедуледтасксфордебугжер | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b4ac6fa753be7672f1e698bda231bd11217c10d4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152731"
---
# <a name="getscheduledtasksfordebugger-method"></a>Метод GetScheduledTasksForDebugger
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает массив всех запланированных задач.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в mscorlib.dll)  
  
 Так как вы не можете получить доступ к этому внутреннему элементу из .NET Framework, на стандартном промежуточном языке (CIL) приведен следующий синтаксис.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Массив всех запланированных задач. Каждая задача является выполненной или завершила свою работу.  
  
## <a name="remarks"></a>Remarks  
 Этот метод не является потокобезопасным и не должен использоваться одновременно с другими экземплярами <xref:System.Threading.Tasks.TaskScheduler> . его следует вызывать из отладчика только в том случае, если отладчик приостановил все остальные потоки.  
  
## <a name="see-also"></a>См. также:  
 [Класс TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)
