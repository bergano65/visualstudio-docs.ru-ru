---
title: CONTEXT_INFO_FIELDS | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 05616ba660af188c26f192b97e29d5b60e04fe8a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100664"
---
# <a name="contextinfofields"></a>CONTEXT_INFO_FIELDS
Указывает, какую информацию для получения о контексте памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_CONTEXT_INFO_FIELDS {   
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
typedef DWORD CONTEXT_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_CONTEXT_INFO_FIELDS {  
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
```  
  
## <a name="members"></a>Участники  
 CIF_MODULEURL  
 Инициализация или использовать `bstrModuleUrl` поле [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) структуры.  
  
 CIF_FUNCTION  
 Инициализация или использовать `bstrFunction` поле `CONTEXT_INFO` структуры.  
  
 CIF_FUNCTIONOFFSET  
 Инициализация или использовать `posFunctionOffset` поле `CONTEXT_INFO` структуры.  
  
 CIF_ADDRESS  
 Инициализация или использовать `bstrAddress` поле `CONTEXT_INFO` структуры.  
  
 CIF_ADDRESSOFFSET  
 Инициализация или использовать `bstrAddressOffset` поле `CONTEXT_INFO` структуры.  
  
 CIF_ALLFIELDS  
 Инициализация или использовать все поля `CONTEXT_INFO` структуры.  
  
## <a name="remarks"></a>Примечания  
 Эти значения передаются параметра [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) метод, чтобы указать, какие поля [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) структуры должны быть инициализированы.  
  
 Эти флаги также используются для указания поля `CONTEXT_INFO` структуры не используются и допустимым при возврате структуры.  
  
 Эти значения могут объединяться с Побитовый оператор или.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)