---
title: Метод Сетнотификатионфорваиткомплетион | Документация Майкрософт
description: Узнайте, как отладчик использует бит состояния, чтобы помочь выйти из тела асинхронного метода для задач в стиле Promise.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 80904e95c1561dd20ed2a6cc9ad561e6c18ee93a
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845223"
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
