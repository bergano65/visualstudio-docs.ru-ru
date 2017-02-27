---
title: "BP_ERROR_RESOLUTION_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_ERROR_RESOLUTION_INFO"
helpviewer_keywords: 
  - "Структура BP_ERROR_RESOLUTION_INFO"
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# BP_ERROR_RESOLUTION_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Описывает разрешение точки останова ошибки, включая расположение программы, а поток.  
  
## Синтаксис  
  
```cpp#  
typedef struct _BP_ERROR_RESOLUTION_INFO {   
   BPERESI_FIELDS         dwFields;  
   BP_RESOLUTION_LOCATION bpResLocation;  
   IDebugProgram2*        pProgram;  
   IDebugThread2*         pThread;  
   BSTR                   bstrMessage;  
   BP_ERROR_TYPE          dwType;  
} BP_ERROR_RESOLUTION_INFO;  
```  
  
```c#  
public struct BP_ERROR_RESOLUTION_INFO {   
   public uint                   dwFields;  
   public BP_RESOLUTION_LOCATION bpResLocation;  
   public IDebugProgram2         pProgram;  
   public IDebugThread2          pThread;  
   public string                 bstrMessage;  
   public uint                   dwType;  
};  
```  
  
## Члены  
 `dwFields`  
 Сочетания значений из [BPERESI\_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) определение перечисления, какие поля этой структуры заполнянны.  
  
 `bpResLocation`  
 [BP\_RESOLUTION\_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) соединение, которое определяет расположение разрешения точки останова.  
  
 `pProgram`  
 IDebugProgram2 объект, который представляет приложение, в котором произошла ошибка точки останова.  
  
 `pThread`  
 IDebugThread2 объект, представляющий поток, в котором приложение, создавшего ошибку точки останова.  
  
 `bstrMessage`  
 Строка, содержащая любые предупреждения или сообщения об ошибке в результате этого разрешения ошибки.  
  
 `dwType`  
 Значение [BP\_ERROR\_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) перечисление, определяющее тип ошибки точки останова.  
  
## Заметки  
 Эта структура возвращается из [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) метод.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)   
 [BPRESI\_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)   
 [BP\_RESOLUTION\_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP\_ERROR\_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)