---
title: "Метод SetNotificationForWaitCompletion | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f5e35933e59fb4d8ff9f13db4bef8c23891bac2f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="setnotificationforwaitcompletion-method"></a>Метод SetNotificationForWaitCompletion
Устанавливает или снимает бит TASK_STATE_WAIT_COMPLETION_NOTIFICATION состояния.  
  
 **Пространство имен:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в библиотеке mscorlib.dll)  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### <a name="parameters"></a>Параметры  
 `enabled`  
  
 `true`Чтобы установить бит; `false` с незаданным бит.  
  
## <a name="exceptions"></a>Исключения  
  
## <a name="remarks"></a>Примечания  
 Отладчик установит этот бит для пошагового вне тела метода async. Если `enabled` — `true`, этот метод должен вызываться только в задачу, которая еще не завершена. Если `enabled` — `false`, этот метод может быть вызван для завершенных задач. В любом случае он должен использоваться только для задачи-обещания.  
  
## <a name="requirements"></a>Требования  
  
## <a name="see-also"></a>См. также  
 [Task-класс](../../extensibility/debugger/task-class-internal-members.md)