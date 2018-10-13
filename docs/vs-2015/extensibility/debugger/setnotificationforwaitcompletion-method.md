---
title: Метод SetNotificationForWaitCompletion | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5654814931904c157f8970ee0a1046820f3be132
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49173372"
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

