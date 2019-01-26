---
title: Поле TASK_STATE_WAITING_ON_CHILDREN | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_WAITING_ON_CHILDREN field, Task class [.NET Framework debug engines]
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 055b0f8a0babfe5b1492a781c5c80b2bfd8c42c8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54918645"
---
# <a name="taskstatewaitingonchildren-field"></a>Поле TASK_STATE_WAITING_ON_CHILDREN
Задача завершения выполнения его делегат и неявно ожидает завершения присоединенных дочерних задач.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в *mscorlib.dll*)  
  
 Так как не удается получить доступ к внутреннему элементу из .NET Framework, следующий синтаксис предоставляется общего промежуточного языка (CIL).  
  
## <a name="syntax"></a>Синтаксис  
  
```csharp  
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)  
```  
  
## <a name="remarks"></a>Примечания  
 Если [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) поле содержит это значение <xref:System.Threading.Tasks.Task.Status%2A> возвращает <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## <a name="see-also"></a>См. также  
 [Класс Task](../../extensibility/debugger/task-class-internal-members.md)