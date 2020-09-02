---
title: CONTEXT_COMPARE | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9cf283cf7239b5ed74e38ca534538a286a477c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179973"
---
# <a name="context_compare"></a>CONTEXT_COMPARE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Задает критерий для сравнения двух контекстов памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 Найдите в списке первый контекст памяти, равный контексту целевой памяти.  
  
 CONTEXT_LESS_THAN  
 Найдите в списке первый контекст памяти, который меньше контекста целевой памяти.  
  
 CONTEXT_GREATER_THAN  
 Найдите в списке первый контекст памяти, превышающий целевой контекст памяти.  
  
 CONTEXT_LESS_THAN_OR_EQUAL  
 Найдите в списке первый контекст памяти, который меньше или равен контексту целевой памяти.  
  
 CONTEXT_GREATER_THAN_OR_EQUAL  
 Найдите в списке первый контекст памяти, который больше или равен контексту целевой памяти.  
  
 CONTEXT_SAME_SCOPE  
 Найдите в списке первый контекст памяти, который находится в той же области, что и контекст целевой памяти.  
  
 CONTEXT_SAME_FUNCTION  
 Найдите в списке первый контекст памяти, который находится в той же функции, что и Целевая область памяти.  
  
 CONTEXT_SAME_MODULE  
 Найдите в списке первый контекст памяти, который находится в том же модуле, что и целевой контекст памяти.  
  
 CONTEXT_SAME_PROCESS  
 Найдите в списке первый контекст памяти, который находится в том же процессе, что и целевой контекст памяти.  
  
## <a name="remarks"></a>Remarks  
 Передается в качестве аргумента в метод [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) .  
  
 Эти значения используются для поиска контекста первой памяти в списке, удовлетворяющего указанным критериям сравнения. Контекст памяти получает список контекста памяти для сравнения с помощью `IDebugMemoryContext2::Compare` метода. Затем возвращается контекст первой памяти в списке, для которого выполняется оператор сравнения `true` .  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Сравнить](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)
