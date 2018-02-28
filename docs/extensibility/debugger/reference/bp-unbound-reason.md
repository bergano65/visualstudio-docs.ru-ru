---
title: "BP_UNBOUND_REASON | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: fa824f71a4b468a131b1ebf31b3dba21bc83032c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="bpunboundreason"></a>BP_UNBOUND_REASON
Предоставляет причина, по которой был свободные точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
typedef DWORD BP_UNBOUND_REASON;  
```  
  
```csharp  
public enum enum_BP_UNBOUND_REASON {   
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
 Код, который содержит точку останова был выгружен.  
  
 BPUR_BREAKPOINT_REBIND  
 Точка останова были привязаны повторно в другом месте. Это может произойти после изменения и продолжить работу, если точка останова перемещается или при привязке точки останова в файл с путем, который больше не является допустимым.  
  
 BPUR_ BREAKPOINT_ERROR  
 Точка останова будет установлено по ошибке после он привязан. Это происходит, управляемый точек останова, состояние которых становятся недействительными.  
  
## <a name="remarks"></a>Примечания  
 Возвращенный [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)