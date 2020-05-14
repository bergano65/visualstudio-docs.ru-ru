---
title: поле TASK_STATE_FAULTED (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_FAULTED field, Task class [.NET Framework debug engines]
ms.assetid: ced826ae-09a9-4acf-af00-a2343d396bb8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1c9bd5b9ec57e652dd7a57ee3434a2525eeeedbe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712691"
---
# <a name="task_state_faulted-field"></a>TASK_STATE_FAULTED поле
Задача завершилась из-за необработанного исключения.

 **Пространство имен:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в *mscorlib.dll*)

 Поскольку вы не можете получить доступ к этому внутреннему члену из рамочного соглашения .NET, следующий синтаксис предоставляется на общем промежуточном языке (CIL).

## <a name="syntax"></a>Синтаксис

```csharp
.field static assembly literal int32 TASK_STATE_FAULTED = int32(0x00400000)
```

## <a name="remarks"></a>Примечания
 Если [поле m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) содержит это <xref:System.Threading.Tasks.Task.Status%2A> значение, имущество возвращается. <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>

## <a name="see-also"></a>См. также
- [Класс Task](../../extensibility/debugger/task-class-internal-members.md)
