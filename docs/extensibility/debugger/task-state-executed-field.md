---
title: Поле TASK_STATE_EXECUTED | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_EXECUTED field, Task class [.NET Framework debug engines]
ms.assetid: 75b8f9d0-b908-40d0-b109-70feaed2ab0c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b7c3bd3c487c7aa979e6cd3c24122465b13ebeb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922601"
---
# <a name="taskstateexecuted-field"></a>Поле TASK_STATE_EXECUTED
Задача выполняется, но еще не завершилась.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в mscorlib.dll)  
  
 Так как не удается получить доступ к внутреннему элементу из .NET Framework, следующий синтаксис предоставляется общего промежуточного языка (CIL).  
  
## <a name="syntax"></a>Синтаксис  
  
```csharp  
.field static assembly literal int32 TASK_STATE_EXECUTED = int32(0x00020000)  
```  
  
## <a name="remarks"></a>Примечания  
 Если [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) поле содержит это значение <xref:System.Threading.Tasks.Task.Status%2A> возвращает <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## <a name="see-also"></a>См. также  
 [Класс Task](../../extensibility/debugger/task-class-internal-members.md)