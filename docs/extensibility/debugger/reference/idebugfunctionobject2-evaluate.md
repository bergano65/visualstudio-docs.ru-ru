---
title: "IDebugFunctionObject2::Evaluate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugFunctionObject2::Evaluate"
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugFunctionObject2::Evaluate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Вызывает функцию и возвращает результат в виде объекта.  
  
## Синтаксис  
  
```cpp#  
HRESULT Evaluate (  
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwEvalFlags,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```c#  
int Evaluate (  
   IDebugObject     ppParams,  
   uint             dwParams,  
   uint             dwEvalFlags,  
   uint             dwTimeout,  
   out IDebugObject ppResult  
);  
```  
  
#### Параметры  
 `ppParams`  
 \[in\] массив IDebugObject объекты, которое представляет входные параметры.  Каждый из этих параметров не был создан с помощью одного из методов создания в этом интерфейсе.  
  
 `dwParams`  
 \[in\] количество параметров `ppParams` массив.  
  
 `dwEvalFlags`  
 \[in\] сочетание пометит из [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) перечисление, указывающее как вычисление, которое нужно выполнить.  
  
 `dwTimeout`  
 \[in\] задает максимальное время, в миллисекундах, ожидания возврата из этого метода.  Используйте **Бесконечно** ждать бесконечно.  
  
 `ppResult`  
 \[out\] возвращает IDebugObject представляет значение функции как объект.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)