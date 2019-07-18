---
title: Метод GetScheduledTasksForDebugger | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49a63462eece9bef09579c7284f72790a3914bc2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353735"
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