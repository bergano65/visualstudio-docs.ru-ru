---
title: "BP_REQUEST_INFO | Microsoft Docs"
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
  - "BP_REQUEST_INFO"
helpviewer_keywords: 
  - "Структура BP_REQUEST_INFO"
ms.assetid: 42a31412-5b6b-47fe-a762-0c2bc769e1cc
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_REQUEST_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Содержит сведения, необходимые для реализации точку останова.  
  
## Синтаксис  
  
```cpp#  
typedef struct _BP_REQUEST_INFO {  
   BPREQI_FIELDS   dwFields;  
   GUID            guidLanguage;  
   BP_LOCATION     bpLocation;  
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   IDebugThread2*  pThread;  
   BSTR            bstrThreadName;  
   BP_CONDITION    bpCondition;  
   BP_PASSCOUNT    bpPassCount;  
   BP_FLAGS        dwFlags;  
} BP_REQUEST_INFO;  
```  
  
```c#  
public struct BP_REQUEST_INFO {  
   public uint           dwFields;  
   public Guid           guidLanguage;  
   public BP_LOCATION    bpLocation;  
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public IDebugThread2  pThread;  
   public string         bstrThreadName;  
   public BP_CONDITION   bpCondition;  
   public BP_PASSCOUNT   bpPassCount;  
   public uint           dwFlags;  
};  
```  
  
## Члены  
 `dwFields`  
 Комбинация из пометит [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) перечисление, которое определяет, какие поля заполнянны.  
  
 `guidLanguage`  
 Идентификатор GUID языка.  
  
 `bpLocation`  
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) структура, определяющая тип расположения точки останова.  
  
 `pProgram`  
 IDebugProgram2 объект, который представляет приложение, в котором точка останова.  
  
 `bstrProgramName`  
 Имя приложения, в котором точка останова.  
  
 `pThread`  
 IDebugThread2 объект, представляющий поток, в котором точка останова.  
  
 `bstrThreadName`  
 Имя потока, в котором точка останова.  
  
 `bpCondition`  
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) структура, которая описывает условия, при которых точка останова сгорит.  
  
 `bpPassCount`  
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) структура, содержащая данные о количестве передачи точки останова.  
  
 `dwFlags`  
 Комбинация из пометит [BP\_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) перечисление, указывающее флаги точки останова.  
  
## Заметки  
 Эта структура возвращается [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) метод.  
  
 Если необходимо получить идентификатор GUID поставщика обработчика отладки ограничение точки останова или точка трассировки см. в разделе [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структура.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP\_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)