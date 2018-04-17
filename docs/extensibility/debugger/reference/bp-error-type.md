---
title: BP_ERROR_TYPE | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 676ec19fec1406d85e6a7d9e66865b2794f72aa6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="bperrortype"></a>BP_ERROR_TYPE
Указывает тип ошибки точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_BP_ERROR_TYPE {   
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
public enum enum_BP_ERROR_TYPE {   
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
 Указывает ошибки отсутствуют точки останова.  
  
 BPET_TYPE_WARNING  
 Указывает ошибки стиле предупреждение точки останова.  
  
 BPET_TYPE_ERROR  
 Указывает ошибку стиля ошибки точки останова.  
  
 BPET_SEV_HIGH  
 Задает точку останова серьезной ошибки.  
  
 BPET_SEV_GENERAL  
 Указывает ошибки серьезность средняя точка останова.  
  
 BPET_SEV_LOW  
 Указывает ошибки низкой важности точки останова.  
  
 BPET_TYPE_MASK  
 Указывает ошибку стиль маски точки останова.  
  
 BPET_SEV_MASK  
 Указывает ошибки серьезность маска стиля точки останова.  
  
 BPET_GENERAL_WARNING  
 Указывает ошибки общие предупреждение стиля точки останова.  
  
 BPET_GENERAL_ERROR  
 Указывает ошибки стиля для ошибки общие точки останова.  
  
 BPET_ALL  
 Указывает типы ошибок все точки останова.  
  
## <a name="remarks"></a>Примечания  
 Эти значения могут объединяться с помощью битового оператора `OR` и используется для `dwType` членом [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) структуры. Переданное в качестве параметра для [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) метод.  
  
 Тип ошибки точки останова состоит из типа и серьезности. Это означает, что тип ошибки точка останова никогда не только типом (например, `BPET_TYPE_ERROR`,) или уровнем серьезности (например, `BPET_SEV_GENERAL`) сам по себе. `BPET_GENERAL_WARNING` и `BPET_GENERAL_ERROR` предоставляют стандартных значений для общих точек останова предупреждения и ошибки.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)