---
title: поле TASK_STATE_EXECUTED Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_EXECUTED field, Task class [.NET Framework debug engines]
ms.assetid: 75b8f9d0-b908-40d0-b109-70feaed2ab0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa637b8bc29f53ca6dde1b13310d83a5e176408f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712703"
---
# <a name="task_state_executed-field"></a>поле TASK_STATE_EXECUTED
Задача выполняется, но еще не завершилась.

 **Пространство имен:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в mscorlib.dll)

 Поскольку вы не можете получить доступ к этому внутреннему члену из рамочного соглашения .NET, следующий синтаксис предоставляется на общем промежуточном языке (CIL).

## <a name="syntax"></a>Синтаксис

```csharp
.field static assembly literal int32 TASK_STATE_EXECUTED = int32(0x00020000)
```

## <a name="remarks"></a>Примечания
 Если [поле m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) содержит это <xref:System.Threading.Tasks.Task.Status%2A> значение, имущество возвращается. <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>

## <a name="see-also"></a>См. также
- [Класс Task](../../extensibility/debugger/task-class-internal-members.md)
