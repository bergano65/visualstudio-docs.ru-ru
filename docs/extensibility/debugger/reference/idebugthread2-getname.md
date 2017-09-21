---
title: "IDebugThread2::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::GetName"
helpviewer_keywords: 
  - "IDebugThread2::GetName"
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugThread2::GetName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает имя потока.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetName (   
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetName (   
   out string pbstrName  
);  
```  
  
#### Параметры  
 `pbstrName`  
 \[out\] возвращает имя потока.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Извлеченное имя всегда имя, можно отобразить, и это имя описывает поток.  Имя потока может быть производным от архитектуры среды выполнения, которая поддерживает именованные потоки или может быть именем производным от обработчика отладки.  Кроме того, имя потока можно задать вызовом [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) метод.  
  
## См. также  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)