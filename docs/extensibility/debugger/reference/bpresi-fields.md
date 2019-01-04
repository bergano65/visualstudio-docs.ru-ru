---
title: BPRESI_FIELDS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bad42049bf10b3b5e0f599ea5b043dd73cabc051
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53931519"
---
# <a name="bpresifields"></a>BPRESI_FIELDS
Указывает сведения, которые требуется получить о успешного разрешения точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
typedef DWORD BPRESI_FIELDS;  
```  
  
```csharp  
public enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
```  
  
## <a name="members"></a>Участники  
 BPRESI_BPRESLOCATION  
 Initialize и использование `bpResLocation` (точки останова разрешения) поле [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) структуры.  
  
 BPRESI_PROGRAM  
 Инициализация и использование `pProgram` поле `BP_RESOLUTION_INFO` структуры.  
  
 BPRESI_THREAD  
 Инициализация и использование `pThread` поле `BP_RESOLUTION_INFO` структуры.  
  
 BPRESI_ALLFIELDS  
 Указывает все поля.  
  
## <a name="remarks"></a>Примечания  
 Передаваемый [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) метод, чтобы указать, какие поля [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) структуры должны быть инициализированы.  
  
 Эти флаги также используются для указания поля `BP_RESOLUTION_INFO` структуры не используются и допустимым при возвращении этой структуре.  
  
 Эти значения могут объединяться с побитовым объектом `OR`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)