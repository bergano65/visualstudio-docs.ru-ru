---
title: Метод SetNotificationForWaitCompletion Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 226ac41c8e3b7427ac3b9aba7bea08dbb7329d16
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712862"
---
# <a name="setnotificationforwaitcompletion-method"></a>Метод SetNotificationForWaitCompletion
Устанавливает или очищает TASK_STATE_WAIT_COMPLETION_NOTIFICATION бит состояния.

 **Пространство имен:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в *mscorlib.dll*)

## <a name="syntax"></a>Синтаксис

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Параметры
 `enabled`

 `true`установить бит; `false` чтобы разгрузить бит.

## <a name="exceptions"></a>Исключения

## <a name="remarks"></a>Примечания
 Отладчик устанавливает этот бит, чтобы помочь выйти из тела метода асин. Если `enabled` `true`есть, этот метод должен вызываться только на задачу, которая еще не завершена. Когда `enabled` `false`это, этот метод может быть вызван на завершенные задачи. В любом случае он должен использоваться только для задач в стиле обещания.

## <a name="requirements"></a>Требования

## <a name="see-also"></a>См. также
- [Класс Task](../../extensibility/debugger/task-class-internal-members.md)
