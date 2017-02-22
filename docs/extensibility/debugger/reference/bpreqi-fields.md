---
title: "BPREQI_FIELDS | Microsoft Docs"
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
  - "BPREQI_FIELDS"
helpviewer_keywords: 
  - "Перечисление BPREQI_FIELDS"
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# BPREQI_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Определяет сведения, которые нужно извлечь о запросе точки останова.  
  
## Синтаксис  
  
```cpp  
enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
typedef DWORD BPREQI_FIELDS;  
```  
  
```c#  
public enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
```  
  
## Члены  
 BPREQI\_BPLOCATION  
 Инициализируйте и использование `bpLocation` \(поле расположение точки останова\)  [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) OR  [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структура.  
  
 BPREQI\_LANGUAGE  
 Инициализируйте и использование `guidLanguage` поле   `BP_REQUEST_INFO` OR  `BP_REQUEST_INFO2` структура.  
  
 BPREQI\_PROGRAM  
 Инициализируйте и использование `pProgram` поле   `BP_REQUEST_INFO` OR  `BP_REQUEST_INFO2` структура.  
  
 BPREQI\_PROGRAMNAME  
 Инициализируйте и использование `bstrProgramName` поле   `BP_REQUEST_INFO` OR  `BP_REQUEST_INFO2` структура.  
  
 BPREQI\_THREAD  
 Инициализируйте и использование `pThread` поле   `BP_REQUEST_INFO` OR  `BP_REQUEST_INFO2` структура.  
  
 BPREQI\_THREADNAME  
 Инициализируйте и использование `bstrThreadName` поле   `BP_REQUEST_INFO` OR  `BP_REQUEST_INFO2` структура.  
  
 BPREQI\_PASSCOUNT  
 Инициализируйте и использование `bpPassCount` поле   `BP_REQUEST_INFO` OR  `BP_REQUEST_INFO2` структура.  
  
 BPREQI\_CONDITION  
 Инициализируйте и использование `bpCondition` \(поле условия точки останова\)   `BP_REQUEST_INFO` OR  `BP_REQUEST_INFO2` структура.  
  
 BPREQI\_FLAGS  
 Инициализируйте и использование `dwFlags` поле   `BP_REQUEST_INFO` OR  `BP_REQUEST_INFO2` структура.  
  
 BPREQI\_ALLOLDFIELDS  
 Инициализируйте и использование все поля `BP_REQUEST_INFO` структура.  
  
 BPREQI\_VENDOR  
 Инициализируйте и использование `guidVendor` поле   `BP_REQUEST_INFO2` структура.  
  
 BPREQI\_CONSTRAINT  
 Инициализируйте и использование `bstrConstraint` поле   `BP_REQUEST_INFO2` структура.  
  
 BPREQI\_TRACEPOINT  
 Инициализируйте и использование `bstrTracepoint` поле   `BP_REQUEST_INFO2` структура.  
  
 BPREQI\_ALLFIELDS  
 Указывает все поля `BP_REQUEST_INFO2` структура.  
  
## Заметки  
 Передается в качестве аргумента [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) и  [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) методы, чтобы указать, какие поля  [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) и  [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структуры следует инициализировать.  
  
 Эти флаги также используются для указания того, какие поля `BP_REQUEST_INFO` и  `BP_REQUEST_INFO2` используемые структуры и допустимы, если каждая структура возвращается.  
  
 Эти значения могут объединяться с побитовый оператор `OR`.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)