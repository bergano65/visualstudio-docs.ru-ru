---
title: CONTEXT_COMPARE | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0563f037f77c18cc5e686c1ea6acf429c91ad06d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108587"
---
# <a name="contextcompare"></a>CONTEXT_COMPARE
Указывает критерии для сравнения двух контекстов памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_CONTEXT_COMPARE {   
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
public enum enum_CONTEXT_COMPARE {   
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
 Найти первый контекст памяти в списке, равное целевой контекст памяти.  
  
 CONTEXT_LESS_THAN  
 Найти первый контекст памяти в списке, который меньше, чем целевой контекст памяти.  
  
 CONTEXT_GREATER_THAN  
 Найти первый контекст памяти в списке, который больше, чем целевой контекст памяти.  
  
 CONTEXT_LESS_THAN_OR_EQUAL  
 Найдите первый контекст памяти в списке, меньше или равно целевой контекст памяти.  
  
 CONTEXT_GREATER_THAN_OR_EQUAL  
 Найти первый контекст памяти в списке, который больше или равно целевой контекст памяти.  
  
 CONTEXT_SAME_SCOPE  
 Найти первый контекст памяти в списке, который находится в той же области, как целевой контекст памяти.  
  
 CONTEXT_SAME_FUNCTION  
 Найти первый контекст памяти в списке, который находится в той же функции, как целевой области памяти.  
  
 CONTEXT_SAME_MODULE  
 Найти первый контекст памяти в списке, который находится в одном модуле с целевой контекст памяти.  
  
 CONTEXT_SAME_PROCESS  
 Найти первый контекст памяти в списке, который находится в том же процессе, как целевой контекст памяти.  
  
## <a name="remarks"></a>Примечания  
 Передается в качестве аргумента для [сравнения](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) метод.  
  
 Эти значения используются для нахождения первого контекст памяти в списке, удовлетворяющий условиям указанного сравнения. Получает контекст памяти список контекстов памяти сравнивать себя с помощью `IDebugMemoryContext2::Compare` метод. Первый контекст памяти в списке, для которого является оператором сравнения `true` затем возвращается.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)