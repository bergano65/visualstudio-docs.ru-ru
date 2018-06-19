---
title: Метод SetNotificationForWaitCompletion | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a005ee7d624604dd716042bd839b48b7a367dd48
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127022"
---
# <a name="setnotificationforwaitcompletion-method"></a>Метод SetNotificationForWaitCompletion
Устанавливает или снимает бит TASK_STATE_WAIT_COMPLETION_NOTIFICATION состояния.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в библиотеке mscorlib.dll)  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### <a name="parameters"></a>Параметры  
 `enabled`  
  
 `true` Чтобы установить бит; `false` с незаданным бит.  
  
## <a name="exceptions"></a>Исключения  
  
## <a name="remarks"></a>Примечания  
 Отладчик установит этот бит для пошагового вне тела метода async. Если `enabled` — `true`, этот метод должен вызываться только в задачу, которая еще не завершена. Если `enabled` — `false`, этот метод может быть вызван для завершенных задач. В любом случае он должен использоваться только для задачи-обещания.  
  
## <a name="requirements"></a>Требования  
  
## <a name="see-also"></a>См. также  
 [Task-класс](../../extensibility/debugger/task-class-internal-members.md)