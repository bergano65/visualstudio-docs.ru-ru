---
title: Поля m_children | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a5d924e0439be2f8ab615d18a61f1303994b8dde
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53923696"
---
# <a name="mchildren-field"></a>поля m_children
Список дочерних задач, которые зарегистрированы с помощью этой задачи.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в *mscorlib.dll*)  
  
 Так как не удается получить доступ к внутреннему элементу из .NET Framework, следующий синтаксис предоставляется общего промежуточного языка (CIL).  
  
## <a name="syntax"></a>Синтаксис  
  
```csharp 
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Примечания  
 Пока выполняется задача, только потоку, который выполняет задачу должен получить доступ к этот массив.  
  
 Если задача завершена, другие потоки могут обращаться к этому полю, пока они не ничего добавлять к нему или удалить любой элемент из него.  
  
## <a name="see-also"></a>См. также  
 [Класс ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)