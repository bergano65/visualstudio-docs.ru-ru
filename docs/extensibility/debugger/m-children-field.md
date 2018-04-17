---
title: m_children поле | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e71bc592e77daac877b571b14acd2d62a8657b9f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="mchildren-field"></a>m_children поля
Список дочерних задач, которые зарегистрированы с помощью этой задачи.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в библиотеке mscorlib.dll)  
  
 Так как не может получить доступ к внутреннему элементу из платформы .NET Framework, синтаксиса предоставляется общего промежуточного языка (CIL).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Примечания  
 Пока выполняется задача, поток, который выполняет задачу следует обращаться к данного массива.  
  
 Если задача завершена, другие потоки могут обращаться к этому полю, пока они не добавлять к нему и ничего удалять из нее.  
  
## <a name="see-also"></a>См. также  
 [Класс ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)