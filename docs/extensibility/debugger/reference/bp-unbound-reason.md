---
title: BP_UNBOUND_REASON | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 72e8975f67925976a0c6c446d798d048068c1ad6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53848039"
---
# <a name="bpunboundreason"></a>BP_UNBOUND_REASON
Предоставляет причину, по которой был отсоединен точку останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
typedef DWORD BP_UNBOUND_REASON;  
```  
  
```csharp  
public enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
```  
  
## <a name="members"></a>Участники  
 BPUR_UNKNOWN  
 Причина неизвестна.  
  
 BPUR_CODE_UNLOADED  
 Код, который содержит точку останова, был выгружен.  
  
 BPUR_BREAKPOINT_REBIND  
 Точка останова были привязаны повторно в другом месте. Это может произойти после изменения и продолжить работу, если точка останова перемещается или привязана точка останова в файл с путем, который больше не является допустимым.  
  
 BPUR_ BREAKPOINT_ERROR  
 Чтобы находиться в состоянии ошибки, после привязки определяется точка останова. Это происходит для управляемых точек останова, условия которых больше не действительны.  
  
## <a name="remarks"></a>Примечания  
 Возвращенный [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)