---
title: "IDebugParsedExpression::EvaluateSync | Microsoft Docs"
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
  - "IDebugParsedExpression::EvaluateSync"
helpviewer_keywords: 
  - "Метод IDebugParsedExpression::EvaluateSync"
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugParsedExpression::EvaluateSync
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод вычисляет проанализированное выражение и при необходимости приводит результат в другой тип данных.  
  
## Синтаксис  
  
```cpp#  
HRESULT EvaluateSync(   
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BSTR                  bstrResultType,  
   IDebugProperty2**     ppResult  
);  
```  
  
```c#  
int EvaluateSync(  
   uint                 dwEvalFlags,   
   uint                 dwTimeout,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   string               bstrResultType,   
   out IDebugProperty2  ppResult  
);  
```  
  
#### Параметры  
 `dwEvalFlags`  
 \[in\] сочетание [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) константы, которые контролируют, как необходимо оценить выражение.  
  
 `dwTimeout`  
 \[in\] задает максимальное время, в миллисекундах, ожидания возврата из этого метода.  Используйте `INFINITE` ждать бесконечно.  
  
 `pSymbolProvider`  
 \[in\] поставщик символов, выраженный как [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) интерфейс.  
  
 `pAddress`  
 \[in\] текущее местоположение выполнения внутри метода, выраженный как [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейс.  
  
 `pBinder`  
 \[in\] связыватель, выраженный как [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) интерфейс.  
  
 `bstrResultType`  
 \[in\] тип результата должен быть приведен к типу.  Этот аргумент может принимать значение NULL.  
  
 `ppResult`  
 \[out\] возвращает IDebugProperty2 интерфейс, представляющий результаты оценки.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Контекст оценки выражений дается by`pAddress`, который позволяет определить, содержащий метод, а затем использовать правила выбора области языка определения значения символов в выражении.  
  
## См. также  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)