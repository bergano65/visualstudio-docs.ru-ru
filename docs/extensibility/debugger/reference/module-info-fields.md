---
title: "MODULE_INFO_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MODULE_INFO_FIELDS"
helpviewer_keywords: 
  - "Перечисление MODULE_INFO_FIELDS"
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# MODULE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Указывает флаги для модуля отладки.  
  
## Синтаксис  
  
```cpp#  
enum enum_MODULE_INFO_FIELDS {   
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
  
```c#  
public enum enum_MODULE_INFO_FIELDS {   
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
  
## Члены  
 MIF\_NONE  
 Инициализируйте и использование ни одно из полей в макете.  
  
 MIF\_NAME  
 Инициализируйте и использование `m_bstrName` поле  [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) структура.  
  
 MIF\_URL  
 Инициализируйте и использование `m_bstrUrl` поле  `MODULE_INFO` структура.  
  
 MIF\_VERSION  
 Инициализируйте и использование `m_bstrVersion` поле  `MODULE_INFO` структура.  
  
 MIF\_DEBUGMESSAGE  
 Инициализируйте и использование `m_bstrDebugMessage` поле  `MODULE_INFO` структура.  
  
 MIF\_LOADADDRESS  
 Инициализируйте и использование `m_addrLoadAddress` поле  `MODULE_INFO` структура.  
  
 MIF\_PREFFEREDADDRESS  
 Инициализируйте и использование `m_addrPreferredLoadAddress` поле  `MODULE_INFO` структура.  
  
 MIF\_SIZE  
 Инициализируйте и использование `m_dwSize` поле  `MODULE_INFO` структура.  
  
 MIF\_LOADORDER  
 Инициализируйте и использование `m_dwLoadOrder` поле  `MODULE_INFO` структура.  
  
 MIF\_TIMESTAMP  
 Инициализируйте и использование `m_TimeStamp` поле  `MODULE_INFO` структура.  
  
 MIF\_URLSYMBOLLOCATION  
 Инициализируйте и использование `m_bstrUrlSymbolLocation` поле  `MODULE_INFO` структура.  
  
 MIF\_FLAGS  
 Инициализируйте и использование `m_dwModuleFlags` поле  `MODULE_INFO` структура.  
  
 MIF\_ALLFIELDS  
 Инициализируйте и использование все поля `MODULE_INFO` структура.  
  
## Заметки  
 Эти значения передаются в качестве аргумента [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) метод, чтобы показать, какие поля  [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) структура быть инициализированным.  
  
 Эти значения также используются в `MODULE_INFO` структура для указания того, какие поля используются и допустимы.  
  
 Эти флаги могут объединяться с побитовый оператор `OR`.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)