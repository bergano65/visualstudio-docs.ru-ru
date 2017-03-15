---
title: "IDebugPort2::GetPortId | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPort2::GetPortId"
helpviewer_keywords: 
  - "IDebugPort2::GetPortId"
ms.assetid: 837cb924-c113-4224-aa86-3e02b33dfa70
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPort2::GetPortId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Получает идентификатор порта.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetPortId(   
   GUID* pguidPort  
);  
```  
  
```c#  
int GetPortId(   
   out Guid pguidPort  
);  
```  
  
#### Параметры  
 `pguidPort`  
 \[out\] возвращает идентификатор GUID, определяющий порт.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)