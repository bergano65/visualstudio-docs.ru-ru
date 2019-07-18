---
title: Метод SetNotificationForWaitCompletion | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 874e31c331f16e760e030f337dda715473b77af8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62423404"
---
# <a name="setnotificationforwaitcompletion-method"></a>Метод SetNotificationForWaitCompletion
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Задает или сбрасывает бит TASK_STATE_WAIT_COMPLETION_NOTIFICATION состояния.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в mscorlib.dll)  
  
## <a name="syntax"></a>Синтаксис  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### <a name="parameters"></a>Параметры  
 `enabled`  
  
 `true` Чтобы установить бит; `false` чтобы бит.  
  
## <a name="exceptions"></a>Исключения  
  
## <a name="remarks"></a>Примечания  
 Отладчик установит этот бит этапе за пределы тела метода async. Если `enabled` является `true`, этот метод должен вызываться только в задачу, которая еще не завершена. Если `enabled` является `false`, этот метод может вызываться для завершенных задач. В любом случае он должен использоваться только для задач стиле promise.  
  
## <a name="requirements"></a>Требования  
  
## <a name="see-also"></a>См. также  
 [Класс Task](../../extensibility/debugger/task-class-internal-members.md)
