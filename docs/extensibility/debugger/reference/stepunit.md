---
title: STEPUNIT | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- STEPUNIT
helpviewer_keywords:
- STEPUNIT enumeration
ms.assetid: cb8441f2-f744-4e73-acfe-ae8542df9649
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2323ed8f539de465776ee1a9aebc9b3c21860cf9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54971183"
---
# <a name="stepunit"></a>STEPUNIT
Указывает единицу шага для пошагового выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_STEPUNIT {   
   STEP_STATEMENT   = 0,  
   STEP_LINE        = 1,  
   STEP_INSTRUCTION = 2  
};  
typedef DWORD STEPUNIT;  
```  
  
```csharp  
enum enum_STEPUNIT {   
   STEP_STATEMENT   = 0,  
   STEP_LINE        = 1,  
   STEP_INSTRUCTION = 2  
};  
```  
  
## <a name="members"></a>Участники  
 STEP_STATEMENT  
 Действия инструкцией.  
  
 STEP_LINE  
 Действия с помощью строки.  
  
 STEP_INSTRUCTION  
 Действия по инструкциям.  
  
## <a name="remarks"></a>Примечания  
 Передается в качестве аргумента для [шаг](../../../extensibility/debugger/reference/idebugprocess3-step.md) метод.  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)