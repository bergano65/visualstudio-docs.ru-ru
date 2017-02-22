---
title: "IDebugFunctionObject::Evaluate | Microsoft Docs"
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
  - "IDebugFunctionObject::Evaluate"
helpviewer_keywords: 
  - "Метод IDebugFunctionObject::Evaluate"
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFunctionObject::Evaluate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Вызывает функцию и возвращает результат в виде объекта.  
  
## Синтаксис  
  
```cpp#  
HRESULT Evaluate(   
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```c#  
int Evaluate(  
   IDebugObject[]   ppParams,   
   IntPtr           dwParams,   
   uint             dwTimeout,   
   out IDebugObject ppResult  
);  
```  
  
#### Параметры  
 `ppParams`  
 \[in\] массив IDebugObject объекты, представляющих входные параметры.  Каждый из этих параметров не был создан с одним из `Create` методы  [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) интерфейс.  
  
 `dwParams`  
 \[in\] количество параметров `ppParams` массив.  
  
 `dwTimeout`  
 \[in\] задает максимальное время, в миллисекундах, ожидания возврата из этого метода.  Используйте `INFINITE` ждать бесконечно.  
  
 `ppResult`  
 \[out\] возвращает IDebugObject представления значения функции как объект.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает код ошибки.  
  
## Заметки  
 Этот метод настраивает и выполняет вызов функции, представленной IDebugFunctionObject объект.  
  
## См. также  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)