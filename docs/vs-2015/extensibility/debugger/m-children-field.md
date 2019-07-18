---
title: Поля m_children | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 749b7a8da2cbdf8377e7f2e1fcb39787e2f42303
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149060"
---
# <a name="mchildren-field"></a>Поле m_children
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Список дочерних задач, которые зарегистрированы с помощью этой задачи.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в mscorlib.dll)  
  
 Так как не удается получить доступ к внутреннему элементу из .NET Framework, следующий синтаксис предоставляется общего промежуточного языка (CIL).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Примечания  
 Пока выполняется задача, только потоку, который выполняет задачу должен получить доступ к этот массив.  
  
 Если задача завершена, другие потоки могут обращаться к этому полю, пока они не ничего добавлять к нему и не удаляйте ничего из него.  
  
## <a name="see-also"></a>См. также  
 [Класс ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)
