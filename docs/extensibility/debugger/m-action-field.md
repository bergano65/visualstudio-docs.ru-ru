---
title: обращение поле | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- m_action field, Task class [.NET Framework debug engines]
ms.assetid: 201838c2-260d-4071-b6c3-f526874e19c9
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c9d5a55f7e91b22a5b9a867991acbfe404a660fe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="maction-field"></a>обращение поля
Делегат, который представляет код, выполняемый в <xref:System.Threading.Tasks.Task> объекта.  
  
 **Пространство имен:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
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