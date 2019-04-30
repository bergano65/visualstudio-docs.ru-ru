---
title: Метод NotifyDebuggerOfWaitCompletion | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28811ba402803d1ddb9a6dd08a18d32db6257386
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889417"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>Метод NotifyDebuggerOfWaitCompletion
Метод заполнитель, используемый как целевой объект точки останова в отладчике. Этот метод не должен быть встроенным или оптимизированного.

 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Сборка:** mscorlib (в *mscorlib.dll*)

## <a name="syntax"></a>Синтаксис

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Примечания
 Этот метод следует вызывать все операции соединения с задачей, если их отладчик уведомлений бита.

## <a name="requirements"></a>Требования

## <a name="see-also"></a>См. также
- [Класс Task](../../extensibility/debugger/task-class-internal-members.md)