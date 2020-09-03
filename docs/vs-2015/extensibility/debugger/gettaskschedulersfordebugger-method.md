---
title: Метод Жеттасксчедулерсфордебугжер | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 995bf40669a4480f6f1ddfe8071a7885a4659c9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152715"
---
# <a name="gettaskschedulersfordebugger-method"></a>Метод GetTaskSchedulersForDebugger
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает массив всех <xref:System.Threading.Tasks.TaskScheduler> объектов, которые активны в данный момент.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в mscorlib.dll)  
  
 Так как вы не можете получить доступ к этому внутреннему элементу из .NET Framework, на стандартном промежуточном языке (CIL) приведен следующий синтаксис.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Массив всех <xref:System.Threading.Tasks.TaskScheduler> объектов, которые в настоящее время активны в данный момент <xref:System.AppDomain> .  
  
## <a name="remarks"></a>Remarks  
 Этот метод не является потокобезопасным и не должен использоваться одновременно с другими экземплярами <xref:System.Threading.Tasks.TaskScheduler> . Он должен вызываться из отладчика только в том случае, если отладчик приостановил все остальные потоки.  
  
## <a name="see-also"></a>См. также:  
 [Класс TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)
