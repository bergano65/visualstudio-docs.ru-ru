---
title: Метод Нотифидебугжерофваиткомплетион | Документация Майкрософт
description: Сведения о методе Нотифидебугжерофваиткомплетион, который является заполнителем, используемым отладчиком в качестве целевой точки останова.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 35571b28287ecdea48a2ff089cb25cf3ed742d60
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606636"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>Метод Нотифидебугжерофваиткомплетион
Метод-заполнитель, используемый отладчиком в качестве цели точки останова. Этот метод не должен быть встроенным или оптимизированным.

 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в *mscorlib.dll*)

## <a name="syntax"></a>Синтаксис

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Remarks
 Все операции JOIN с задачей должны вызывать этот метод, если задан бит уведомления отладчика.

## <a name="requirements"></a>Требования

## <a name="see-also"></a>См. также раздел
- [Класс Task](../../extensibility/debugger/task-class-internal-members.md)
