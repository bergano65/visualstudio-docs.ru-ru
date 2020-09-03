---
title: Метод Сетнотификатионфорваиткомплетион | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712862"
---
# <a name="setnotificationforwaitcompletion-method"></a>Метод SetNotificationForWaitCompletion
Задает или очищает бит состояния TASK_STATE_WAIT_COMPLETION_NOTIFICATION.

 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в *mscorlib.dll*)

## <a name="syntax"></a>Синтаксис

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Параметры
 `enabled`

 `true` значение бита; `false` значение, чтобы отменить бит.

## <a name="exceptions"></a>Исключения

## <a name="remarks"></a>Remarks
 Отладчик задает этот бит, чтобы помочь выйти из тела асинхронного метода. Если `enabled` имеет значение `true` , этот метод должен вызываться только для задачи, которая еще не завершена. Если `enabled` имеет это `false` , этот метод может быть вызван для завершенных задач. В любом из событий его следует использовать только для задач в стиле Promise.

## <a name="requirements"></a>Требования

## <a name="see-also"></a>См. также раздел
- [Класс Task](../../extensibility/debugger/task-class-internal-members.md)
