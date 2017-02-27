---
title: "IDebugProviderProgramNode2::UnmarshalDebuggeeInterface | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProviderProgramNode2::UnmarshalDebuggeeInterface"
helpviewer_keywords: 
  - "IDebugProviderProgramNode2::UnmarshalDebuggeeInterface"
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает указанный интерфейс через границы процессов.  
  
## Синтаксис  
  
```cpp  
HRESULT UnmarshalDebuggeeInterface(  
   REFIID riid,  
   void** ppvObject  
);  
```  
  
```c#  
int UnmarshalDebuggeeInterface(  
   ref Guid   riid,  
   out IntPtr ppvObject  
);  
```  
  
#### Параметры  
 `riid`  
 \[in\] идентификатор GUID интерфейса, который необходимо получить.  
  
 `ppvObject`  
 \[out\] возвращает объект, реализующий необходимый интерфейс.  \[C\+\+\] это может быть приведен непосредственно к необходимому типу интерфейса.  Используйте \[c\#\] <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> метод, чтобы получить нужный интерфейс.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Этот метод используется, когда отладчик запускается в [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пространство процесса и отлаживанными программы работают в своей собственной пространстве процесса.  
  
## См. также  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)