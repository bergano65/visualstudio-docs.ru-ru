---
title: MODULE_INFO_FIELDS | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fcc6bd76a4a9aecade72347613ed4f36968c65eb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="moduleinfofields"></a>MODULE_INFO_FIELDS
Задает флаги для модуля отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
typedef DWORD MODULE_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
```  
  
## <a name="members"></a>Участники  
 MIF_NONE  
 Инициализация или использовать ни одно из полей в структуре.  
  
 MIF_NAME  
 Инициализация или использовать `m_bstrName` в [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) структуры.  
  
 MIF_URL  
 Инициализация или использовать `m_bstrUrl` в `MODULE_INFO` структуры.  
  
 MIF_VERSION  
 Инициализация или использовать `m_bstrVersion` в `MODULE_INFO` структуры.  
  
 MIF_DEBUGMESSAGE  
 Инициализация или использовать `m_bstrDebugMessage` в `MODULE_INFO` структуры.  
  
 MIF_LOADADDRESS  
 Инициализация или использовать `m_addrLoadAddress` в `MODULE_INFO` структуры.  
  
 MIF_PREFFEREDADDRESS  
 Инициализация или использовать `m_addrPreferredLoadAddress` в `MODULE_INFO` структуры.  
  
 MIF_SIZE  
 Инициализация или использовать `m_dwSize` в `MODULE_INFO` структуры.  
  
 MIF_LOADORDER  
 Инициализация или использовать `m_dwLoadOrder` в `MODULE_INFO` структуры.  
  
 MIF_TIMESTAMP  
 Инициализация или использовать `m_TimeStamp` в `MODULE_INFO` структуры.  
  
 MIF_URLSYMBOLLOCATION  
 Инициализация или использовать `m_bstrUrlSymbolLocation` в `MODULE_INFO` структуры.  
  
 MIF_FLAGS  
 Инициализация или использовать `m_dwModuleFlags` в `MODULE_INFO` структуры.  
  
 MIF_ALLFIELDS  
 Инициализация или использовать все поля в `MODULE_INFO` структуры.  
  
## <a name="remarks"></a>Примечания  
 Эти значения передаются в качестве аргумента для [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) метод, чтобы указать, какие поля [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) структуры должны быть инициализированы.  
  
 Эти значения также используются в `MODULE_INFO` структуры указывает, какие поля используются и допустимым.  
  
 Эти флаги могут объединяться с битовой `OR`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)