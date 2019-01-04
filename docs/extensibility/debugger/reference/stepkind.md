---
title: STEPKIND | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- STEPKIND
helpviewer_keywords:
- STEPKIND enumeration
ms.assetid: d3d8cf76-24bf-455e-803e-0e3e28f0b262
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c11bae91dfac04dd71932aeef949bae5c15de17e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53920343"
---
# <a name="stepkind"></a>STEPKIND
Задает тип шага для пошагового выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_STEPKIND {   
   STEP_INTO      = 0,  
   STEP_OVER      = 1,  
   STEP_OUT       = 2,  
   STEP_BACKWARDS = 3  
};  
typedef DWORD STEPKIND;  
```  
  
```csharp  
public enum enum_STEPKIND {   
   STEP_INTO      = 0,  
   STEP_OVER      = 1,  
   STEP_OUT       = 2,  
   STEP_BACKWARDS = 3  
};  
```  
  
## <a name="members"></a>Участники  
 STEP_INTO  
 Шаг с заходом в функцию.  
  
 STEP_OVER  
 Шаги с обходом функции.  
  
 STEP_OUT  
 Выходит из функции.  
  
 STEP_BACKWARDS  
 Переход обратно в функцию.  
  
## <a name="remarks"></a>Примечания  
 Передается в качестве аргумента для [шаг](../../../extensibility/debugger/reference/idebugprocess3-step.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)