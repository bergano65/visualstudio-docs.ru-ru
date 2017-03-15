---
title: "BP_ERROR_TYPE | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 07248d28d34373176f9897472c39c0756012da59
ms.lasthandoff: 02/22/2017

---
# <a name="bperrortype"></a>BP_ERROR_TYPE
Указывает тип ошибки точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
  
```c#  
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
  
## <a name="members"></a>Члены  
 BPET_NONE  
 Указывает ошибки отсутствуют точки останова.  
  
 BPET_TYPE_WARNING  
 Задает стиль предупреждение точки останова ошибку.  
  
 BPET_TYPE_ERROR  
 Указывает ошибку стиля ошибки точки останова.  
  
 BPET_SEV_HIGH  
 Задает точку останова серьезной ошибки.  
  
 BPET_SEV_GENERAL  
 Задает средний уровень опасности останова ошибку.  
  
 BPET_SEV_LOW  
 Задает точку останова Низкая важность ошибку.  
  
 BPET_TYPE_MASK  
 Задает стиль маски ошибку точки останова.  
  
 BPET_SEV_MASK  
 Задает серьезность маска стиля останова ошибку.  
  
 BPET_GENERAL_WARNING  
 Задает точку останова общие предупреждение стиля ошибку.  
  
 BPET_GENERAL_ERROR  
 Задает точку останова Общие ошибки стиля ошибку.  
  
 BPET_ALL  
 Задает все типы точек останова ошибок.  
  
## <a name="remarks"></a>Примечания  
 Эти значения могут объединяться с помощью побитовой операции `OR` и используется для `dwType` членом [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) структуры. Передается в качестве параметра для [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) метод.  
  
 Тип ошибки точки останова состоит из типа и серьезности. Это означает, что тип ошибки точки останова никогда не только тип (например, `BPET_TYPE_ERROR`,) или уровнем серьезности (например, `BPET_SEV_GENERAL`) сам по себе. `BPET_GENERAL_WARNING`и `BPET_GENERAL_ERROR` предоставляют стандартные значения для общих точек останова предупреждения и ошибки.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
