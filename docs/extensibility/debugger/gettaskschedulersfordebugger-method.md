---
title: Метод Жеттасксчедулерсфордебугжер | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a3b0c8c16b10a4cf2268161d8a2db96c10303b1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738645"
---
# <a name="gettaskschedulersfordebugger-method"></a>Метод GetTaskSchedulersForDebugger
Извлекает массив всех <xref:System.Threading.Tasks.TaskScheduler> объектов, которые активны в данный момент.

 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в *mscorlib.dll*)

 Так как вы не можете получить доступ к этому внутреннему элементу из .NET Framework, на стандартном промежуточном языке (CIL) приведен следующий синтаксис.

## <a name="syntax"></a>Синтаксис

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Возвращаемое значение
 Массив всех <xref:System.Threading.Tasks.TaskScheduler> объектов, которые в настоящее время активны в данный момент <xref:System.AppDomain> .

## <a name="remarks"></a>Remarks
 Этот метод не является потокобезопасным, и его нельзя использовать параллельно с другими экземплярами <xref:System.Threading.Tasks.TaskScheduler> . Вызывайте этот метод из отладчика только в том случае, если отладчик приостановил все остальные потоки.

## <a name="see-also"></a>См. также раздел
- [Класс TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)
