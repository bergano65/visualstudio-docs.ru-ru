---
title: "IDebugProgramPublisher2::SetDebuggerPresent | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramPublisher2::SetDebuggerPresent"
helpviewer_keywords: 
  - "IDebugProgramPublisher2::SetDebuggerPresent"
ms.assetid: c88c3ff4-3632-4199-b5de-83c6d21bcf75
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugProgramPublisher2::SetDebuggerPresent
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Указывает издатель, что отладчик присутствует и выполнение программы.  
  
## Синтаксис  
  
```cpp  
HRESULT SetDebuggerPresent(  
   BOOL fDebuggerPresent  
);  
```  
  
```c#  
int SetDebuggerPresent(  
   int fDebuggerPresent  
);  
```  
  
#### Параметры  
 `fDebuggerPresent`  
 \[in\] ненулевое значение \(`TRUE`если он присутствует\), ноль \(`FALSE`\), если он отсутствует.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Наличие или отсутствие отладчика отражаются в возвращенных данных [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) метод: значение, возвращаемое при наличии установлен или снят предыдущим вызовом метода  `SetDebuggerPresent` метод.  
  
## См. также  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)