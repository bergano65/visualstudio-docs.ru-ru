---
title: Метод GetScheduledTasksForDebugger | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 221a1b49bd3083e0d2dd0248cdf182d699423057
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56695886"
---
# <a name="getscheduledtasksfordebugger-method"></a>Метод GetScheduledTasksForDebugger
Извлекает массив всех запланированных заданий.

 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в *mscorlib.dll*)

 Так как не удается получить доступ к внутреннему элементу из .NET Framework, следующий синтаксис предоставляется общего промежуточного языка (CIL).

## <a name="syntax"></a>Синтаксис

```csharp
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed
```

## <a name="return-value"></a>Возвращаемое значение
 Массив всех запланированных задач. Каждая задача выполняется или завершено выполнение.

## <a name="remarks"></a>Примечания
 Этот метод не является потокобезопасным и его не следует использовать одновременно с другими экземплярами <xref:System.Threading.Tasks.TaskScheduler>. Этот метод следует вызывайте из отладчика, только в том случае, если отладчик приостановил всех остальных потоков.

## <a name="see-also"></a>См. также
- [Класс TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)