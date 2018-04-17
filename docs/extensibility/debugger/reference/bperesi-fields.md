---
title: BPERESI_FIELDS | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2280740766e20a048f57e58590cc529d98b85264
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="bperesifields"></a>BPERESI_FIELDS
Определяет сведения получить о неудачных разрешении точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD BPERESI_FIELDS;  
```  
  
```csharp  
public enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>Участники  
 PERESI_BPRESLOCATION  
 Инициализация или использовать `bpResLocation` поле (точки останова разрешения) [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) структуры.  
  
 BPERESI_PROGRAM  
 Инициализация или использовать `pProgram` поле `BP_ERROR_RESOLUTION_INFO` структуры.  
  
 BPERESI_THREAD  
 Инициализация или использовать `pThread` поле `BP_ERROR_RESOLUTION_INFO` структуры.  
  
 BPERESI_MESSAGE  
 Инициализация или использовать `bstrMessage` поле `BP_ERROR_RESOLUTION_INFO` структуры.  
  
 BPERESI_TYPE  
 Инициализация или использовать `dwType` (тип точки останова) поле `BP_ERROR_RESOLUTION_INFO` структуры.  
  
 BPERESI_ALLFIELDS  
 Инициализация или использовать все поля `BP_ERROR_RESOLUTION_INFO` структуры.  
  
## <a name="remarks"></a>Примечания  
 Переданное в качестве параметра для [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) метод, чтобы указать, какие поля [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) структуры должны быть инициализированы.  
  
 Эти значения также используются для указания того, какие поля в `BP_ERROR_RESOLUTION_INFO` структуры не используется и допустимым при возврате этой структуры.  
  
 Эти значения могут объединяться с помощью битового оператора `OR`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)