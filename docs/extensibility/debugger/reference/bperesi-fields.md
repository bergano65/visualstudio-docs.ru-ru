---
title: "BPERESI_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BPERESI_FIELDS"
helpviewer_keywords: 
  - "Перечисление BPERESI_FIELDS"
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# BPERESI_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Определяет сведения, которые необходимо извлечь сведения о разрешении ошибок точки останова.  
  
## Синтаксис  
  
```cpp#  
enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD BPERESI_FIELDS;  
```  
  
```c#  
public enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
```  
  
## Члены  
 PERESI\_BPRESLOCATION  
 Инициализируйте и использование `bpResLocation` \(поле расположение разрешения точки останова\)  [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) структура.  
  
 BPERESI\_PROGRAM  
 Инициализируйте и использование `pProgram` поле   `BP_ERROR_RESOLUTION_INFO` структура.  
  
 BPERESI\_THREAD  
 Инициализируйте и использование `pThread` поле   `BP_ERROR_RESOLUTION_INFO` структура.  
  
 BPERESI\_MESSAGE  
 Инициализируйте и использование `bstrMessage` поле   `BP_ERROR_RESOLUTION_INFO` структура.  
  
 BPERESI\_TYPE  
 Инициализируйте и использование `dwType` поле \(тип точки останова\)  `BP_ERROR_RESOLUTION_INFO` структура.  
  
 BPERESI\_ALLFIELDS  
 Инициализируйте и использование все поля `BP_ERROR_RESOLUTION_INFO` структура.  
  
## Заметки  
 Передается как параметр [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) метод, чтобы показать, какие поля  [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) структура быть инициализированным.  
  
 Эти значения также используются для указания того, какие поля `BP_ERROR_RESOLUTION_INFO` используемая структура и допустимы, когда эта структура возвращается.  
  
 Эти значения могут объединяться с побитовый оператор `OR`.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)