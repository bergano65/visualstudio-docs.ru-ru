---
title: BP_ERROR_TYPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3c16d3a9658f2e53a651f7a5201bc5f04d48413c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989481"
---
# <a name="bperrortype"></a>BP_ERROR_TYPE
Указывает тип ошибки точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
typedef DWORD BP_ERROR_TYPE;  
```  
  
```csharp  
public enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
```  
  
## <a name="members"></a>Участники  
 BPET_NONE  
 Указывает ошибки не точки останова.  
  
 BPET_TYPE_WARNING  
 Идентифицирует ошибку стиле предупреждение точки останова.  
  
 BPET_TYPE_ERROR  
 Указывает ошибку стиля ошибки точки останова.  
  
 BPET_SEV_HIGH  
 Идентифицирует ошибку точки останова с высокой важностью.  
  
 BPET_SEV_GENERAL  
 Идентифицирует ошибку серьезности средняя точка останова.  
  
 BPET_SEV_LOW  
 Идентифицирует ошибку низкая серьезность точки останова.  
  
 BPET_TYPE_MASK  
 Идентифицирует ошибку стиле маска точки останова.  
  
 BPET_SEV_MASK  
 Идентифицирует ошибку серьезности маска style точки останова.  
  
 BPET_GENERAL_WARNING  
 Идентифицирует ошибку общие предупреждение style точки останова.  
  
 BPET_GENERAL_ERROR  
 Идентифицирует ошибку общие стиля ошибки точки останова.  
  
 BPET_ALL  
 Указывает типы ошибок все точки останова.  
  
## <a name="remarks"></a>Примечания  
 Эти значения могут объединяться с помощью побитовой `OR` и используются для `dwType` членом [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) структуры. Переданный в качестве параметра для [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) метод.  
  
 Тип ошибки точки останова представляет собой тип и уровень серьезности. Это означает, что тип ошибки точки останова никогда не является только типа (например, `BPET_TYPE_ERROR`,) или уровнем серьезности (например, `BPET_SEV_GENERAL`) сама по себе. `BPET_GENERAL_WARNING` и `BPET_GENERAL_ERROR` предоставляют предварительно определенные значения для общих точек останова предупреждений и ошибок.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)