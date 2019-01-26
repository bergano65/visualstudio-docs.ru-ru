---
title: Метод SetNotificationForWaitCompletion | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c674057d57e5e89a6ed92f56df8606b1a0280fc2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54989449"
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
 [Класс Task](../../extensibility/debugger/task-class-internal-members.md)