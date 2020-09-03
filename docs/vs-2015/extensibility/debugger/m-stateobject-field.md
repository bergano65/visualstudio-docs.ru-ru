---
title: m_stateObject поле | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8e9cfc6f689504bef2a8366f90282641d1e9e105
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149043"
---
# <a name="m_stateobject-field"></a>Поле m_stateObject
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Объект, представляющий данные, которые будет использовать действие.  
  
 **Пространство имен:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Сборка:** mscorlib (в mscorlib.dll)  
  
 Так как вы не можете получить доступ к этому внутреннему элементу из .NET Framework, на стандартном промежуточном языке (CIL) приведен следующий синтаксис.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
.field assembly object m_stateObject  
```  
  
## <a name="remarks"></a>Remarks  
 Это `state` параметр в <xref:System.Threading.Tasks.Task.%23ctor%2A> конструкторе. Это также резервное поле для <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> Свойства.  
  
## <a name="see-also"></a>См. также:  
 [Класс Task](../../extensibility/debugger/task-class-internal-members.md)
