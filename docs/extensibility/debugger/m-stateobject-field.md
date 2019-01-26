---
title: m_stateObject поле | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8718a45f0a2d8ef3075a9c390a756e3ec50062f9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55028716"
---
# <a name="mstateobject-field"></a>поле m_stateObject
Объект, представляющий данные, которые будет использовать действие.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в *mscorlib.dll*)  
  
 Так как не удается получить доступ к внутреннему элементу из .NET Framework, следующий синтаксис предоставляется общего промежуточного языка (CIL).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
.field assembly object m_stateObject  
```  
  
## <a name="remarks"></a>Примечания  
 Это `state` параметр в <xref:System.Threading.Tasks.Task.%23ctor%2A> конструктор. Это также резервное поле для <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> свойство.  
  
## <a name="see-also"></a>См. также  
 [Класс Task](../../extensibility/debugger/task-class-internal-members.md)