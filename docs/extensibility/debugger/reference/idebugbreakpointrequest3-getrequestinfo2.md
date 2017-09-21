---
title: "IDebugBreakpointRequest3::GetRequestInfo2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointRequest3::GetRequestInfo2"
helpviewer_keywords: 
  - "IDebugBreakpointRequest3::GetRequestInfo2"
ms.assetid: 33942e4a-0a0a-49e8-a693-004954f6d38a
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugBreakpointRequest3::GetRequestInfo2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод получает данные запроса точки останова, описывающий этот запрос точки останова.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetRequestInfo2(  
   BPREQI_FIELDS      dwFields,  
   BP_REQUEST_INFO2*  bBPRequestInfo  
);  
```  
  
```c#  
int GetRequestInfo2(  
   enum_BPREQI_FIELDS  dwFields,   
   BP_REQUEST_INFO2[]  bBPRequestInfo  
);  
```  
  
#### Параметры  
 `dwFields`  
 \[in\] сочетание пометит из [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) перечисление, указывающее которых полей  `pBPRequestInfo` можно заполнять in.  
  
 `bBPRequestInfo`  
 \[out\] [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структура, которую требуется заполнить.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Дополнительные сведения в этом запросе, чем возврат из [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) метод.  
  
## См. также  
 [IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)