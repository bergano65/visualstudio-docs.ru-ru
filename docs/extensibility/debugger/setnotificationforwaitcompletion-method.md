---
title: Метод SetNotificationForWaitCompletion | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5d9bee2579cc3a93f657291551955f0c9b7565b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348586"
---
# <a name="setnotificationforwaitcompletion-method"></a>Метод SetNotificationForWaitCompletion
Задает или сбрасывает бит TASK_STATE_WAIT_COMPLETION_NOTIFICATION состояния.

 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в *mscorlib.dll*)

## <a name="syntax"></a>Синтаксис

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Параметры
 `enabled`

 `true` Чтобы установить бит; `false` чтобы бит.

## <a name="exceptions"></a>Исключения

## <a name="remarks"></a>Примечания
 Отладчик установит этот бит этапе за пределы тела метода async. Если `enabled` является `true`, этот метод должен вызываться только в задачу, которая еще не завершена. Когда `enabled` является `false`, этот метод может вызываться для завершенных задач. В любом случае он должен использоваться только для задач стиле promise.

## <a name="requirements"></a>Требования

## <a name="see-also"></a>См. также
- [Класс Task](../../extensibility/debugger/task-class-internal-members.md)