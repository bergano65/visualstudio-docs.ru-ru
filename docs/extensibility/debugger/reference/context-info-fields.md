---
title: "CONTEXT_INFO_FIELDS | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CONTEXT_INFO_FIELDS
helpviewer_keywords: CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e604dc09215ac98b2c23fe85312e281b306e9961
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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
  
## <a name="members"></a>Члены  
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