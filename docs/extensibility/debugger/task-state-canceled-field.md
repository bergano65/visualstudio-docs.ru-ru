---
title: Поле TASK_STATE_CANCELED | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_CANCELED field, Task class [.NET Framework debug engines]
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b022daee6e71cd0728c2c161eb3e75a865304d04
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912731"
---
# <a name="taskstatecanceled-field"></a>Поле TASK_STATE_CANCELED
Задача отменена, прежде чем достигнут состояние, либо подтверждения его отмены и завершена без исключения.

 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в mscorlib.dll)

 Так как не удается получить доступ к внутреннему элементу из .NET Framework, следующий синтаксис предоставляется общего промежуточного языка (CIL).

## <a name="syntax"></a>Синтаксис

```csharp
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)
```

## <a name="remarks"></a>Примечания
 Если [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) поле содержит это значение <xref:System.Threading.Tasks.Task.Status%2A> возвращает <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.

## <a name="see-also"></a>См. также
- [Класс Task](../../extensibility/debugger/task-class-internal-members.md)