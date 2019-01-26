---
title: Метод GetTaskSchedulersForDebugger | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 76229d86c973c9ef512ecf5039ae420085129160
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55029249"
---
# <a name="gettaskschedulersfordebugger-method"></a>Метод GetTaskSchedulersForDebugger
Получает массив всех <xref:System.Threading.Tasks.TaskScheduler> объектов, которые активны в текущий момент.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в *mscorlib.dll*)  
  
 Так как не удается получить доступ к внутреннему элементу из .NET Framework, следующий синтаксис предоставляется общего промежуточного языка (CIL).  
  
## <a name="syntax"></a>Синтаксис  
  
```csharp  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Массив всех <xref:System.Threading.Tasks.TaskScheduler> объектов, которые активны в текущий момент в этом <xref:System.AppDomain>.  
  
## <a name="remarks"></a>Примечания  
 Этот метод не является потокобезопасным и его не следует использовать одновременно с другими экземплярами <xref:System.Threading.Tasks.TaskScheduler>. Этот метод следует вызывайте из отладчика, только в том случае, если отладчик приостановил всех остальных потоков.  
  
## <a name="see-also"></a>См. также  
 [Класс TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)