---
title: CONTEXT_COMPARE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95706df8b9b4d366e8baf25a96e3e15bc6532be1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54930216"
---
# <a name="contextcompare"></a>CONTEXT_COMPARE
Указывает критерии для сравнения двух контекстах памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
typedef DWORD CONTEXT_COMPARE;  
```  
  
```csharp  
public enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
```  
  
## <a name="members"></a>Участники  
 CONTEXT_EQUAL  
 Найдите первый контекст памяти в списке, равный целевой контекст памяти.  
  
 CONTEXT_LESS_THAN  
 Найти первый контекст памяти в списке, который меньше, чем целевой контекст памяти.  
  
 CONTEXT_GREATER_THAN  
 Найти первый контекст памяти в списке, который больше, чем целевой контекст памяти.  
  
 CONTEXT_LESS_THAN_OR_EQUAL  
 Найти первый контекст памяти в списке, которое меньше или равно целевой контекст памяти.  
  
 CONTEXT_GREATER_THAN_OR_EQUAL  
 Найти первый контекст памяти в списке, который больше или равна целевой контекст памяти.  
  
 CONTEXT_SAME_SCOPE  
 Найти первый контекст памяти в списке, который находится в той же области, что целевой контекст памяти.  
  
 CONTEXT_SAME_FUNCTION  
 Найти первый контекст памяти в списке, который находится в ту же функцию, что целевой области памяти.  
  
 CONTEXT_SAME_MODULE  
 Найти первый контекст памяти в списке, который находится в одном модуле с целевой контекст памяти.  
  
 CONTEXT_SAME_PROCESS  
 Найдите первый контекст памяти в списке, в том же процессе, что целевой контекст памяти.  
  
## <a name="remarks"></a>Примечания  
 Передается в качестве аргумента для [сравнения](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) метод.  
  
 Эти значения используются для поиска первого контекста памяти в списке, который удовлетворяет условиям указанного сравнения. Контекст памяти предоставляется список контекстов памяти сравнивать себя с помощью `IDebugMemoryContext2::Compare` метод. Первый контекст памяти в списке, для которого является оператор сравнения `true` затем возвращается.  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)