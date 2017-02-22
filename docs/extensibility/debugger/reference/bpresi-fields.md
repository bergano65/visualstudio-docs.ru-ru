---
title: "BPRESI_FIELDS | Microsoft Docs"
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
  - "BPRESI_FIELDS"
helpviewer_keywords: 
  - "Перечисление BPRESI_FIELDS"
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# BPRESI_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Определяет сведения, которые нужно извлечь об успешном разрешении точки останова.  
  
## Синтаксис  
  
```cpp#  
enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
typedef DWORD BPRESI_FIELDS;  
```  
  
```c#  
public enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
```  
  
## Члены  
 BPRESI\_BPRESLOCATION  
 Инициализируйте и использование `bpResLocation` \(поле расположение разрешения точки останова\)  [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) структура.  
  
 BPRESI\_PROGRAM  
 Инициализируйте и использование `pProgram` поле   `BP_RESOLUTION_INFO` структура.  
  
 BPRESI\_THREAD  
 Инициализируйте и использование `pThread` поле   `BP_RESOLUTION_INFO` структура.  
  
 BPRESI\_ALLFIELDS  
 Указывает все поля.  
  
## Заметки  
 Передается методу [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) метод, чтобы показать, какие поля  [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) структура быть инициализированным.  
  
 Эти флаги также используются для указания того, какие поля `BP_RESOLUTION_INFO` используемая структура и допустимы, когда эта структура возвращается.  
  
 Эти значения могут объединяться с побитовый оператор `OR`.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)