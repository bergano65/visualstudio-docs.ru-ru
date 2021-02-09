---
title: Метод Жетсчедуледтасксфордебугжер | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 318e535d86dcd51f9c9bbfcfae8e228c8d7c20b4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921351"
---
# <a name="getscheduledtasksfordebugger-method"></a>Метод GetScheduledTasksForDebugger
Извлекает массив всех запланированных задач.

 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в *mscorlib.dll*)

 Так как вы не можете получить доступ к этому внутреннему элементу из платформа .NET Framework, на стандартном промежуточном языке (CIL) приведен следующий синтаксис.

## <a name="syntax"></a>Синтаксис

```csharp
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed
```

## <a name="return-value"></a>Возвращаемое значение
 Массив всех запланированных задач. Каждая задача является выполненной или завершила свою работу.

## <a name="remarks"></a>Remarks
 Этот метод не является потокобезопасным, и его нельзя использовать параллельно с другими экземплярами <xref:System.Threading.Tasks.TaskScheduler> . Вызывайте этот метод из отладчика только в том случае, если отладчик приостановил все остальные потоки.

## <a name="see-also"></a>См. также раздел
- [Класс TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)
