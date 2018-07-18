---
title: обращение поле | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_action field, Task class [.NET Framework debug engines]
ms.assetid: 201838c2-260d-4071-b6c3-f526874e19c9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5bd045c19b08ec5b3ba5db71e72e6380e65093a7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109253"
---
# <a name="maction-field"></a>обращение поля
Делегат, который представляет код, выполняемый в <xref:System.Threading.Tasks.Task> объекта.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в библиотеке mscorlib.dll)  
  
 Так как не может получить доступ к внутреннему элементу из платформы .NET Framework, синтаксиса предоставляется общего промежуточного языка (CIL).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
.field assembly object m_action  
```  
  
## <a name="remarks"></a>Примечания  
 Это `action` параметр в <xref:System.Threading.Tasks.Task.%23ctor%2A> конструктора.  
  
## <a name="see-also"></a>См. также  
 [Task-класс](../../extensibility/debugger/task-class-internal-members.md)