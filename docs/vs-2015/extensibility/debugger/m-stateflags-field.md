---
title: m_stateFlags поле | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_stateFlags field, Task class [.NET Framework debug engines]
ms.assetid: 82b20efc-08f2-4cd2-91f6-4e01e3da906b
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 794ab8baac441fc14d41c2d30b9db4b0894e88e8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052380"
---
# <a name="mstateflags-field"></a>Поле m_stateFlags
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Хранит сведения о текущем состоянии <xref:System.Threading.Tasks.Task> объекта.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в mscorlib.dll)  
  
 Так как не удается получить доступ к внутреннему элементу из .NET Framework, следующий синтаксис предоставляется общего промежуточного языка (CIL).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
.field assembly int32 modreq(System.Runtime.CompilerServices.IsVolatile) m_stateFlags  
```  
  
## <a name="remarks"></a>Примечания  
 Как правило, используется <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=fullName> свойство для доступа к этому значению.  
  
 Этот член может быть любое сочетание следующих значений:  
  
- [TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)  
  
- [TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)  
  
- [TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)  
  
- [TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)  
  
- [TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)  
  
## <a name="see-also"></a>См. также  
 [Класс Task](../../extensibility/debugger/task-class-internal-members.md)
