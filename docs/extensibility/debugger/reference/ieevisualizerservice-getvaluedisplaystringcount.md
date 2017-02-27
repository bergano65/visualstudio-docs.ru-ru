---
title: "IEEVisualizerService::GetValueDisplayStringCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IEEVisualizerService::GetValueDisplayStringCount"
  - "GetValueDisplayStringCount"
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IEEVisualizerService::GetValueDisplayStringCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Извлекает число строк значения для отображения указанного свойства или поля.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetValueDisplayStringCount (  
   DWORD         displayKind,   
   IDebugField * propertyOrField,   
   ULONG *       pcelt  
);  
```  
  
```c#  
int GetValueDisplayStringCount (  
   uint        displayKind,   
   IDebugField propertyOrField,   
   out ulong   pcelt  
);  
```  
  
#### Параметры  
 `displayKind`  
 \[in\] значение [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) перечисление.  
  
 `propertyOrField`  
 \[in\] IDebugField интерфейс, представляющий свойство или поле.  
  
 `pcelt`  
 \[out\] возвращает число строк значения для отображения.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)