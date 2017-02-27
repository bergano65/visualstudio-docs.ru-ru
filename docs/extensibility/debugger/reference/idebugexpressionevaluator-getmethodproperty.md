---
title: "IDebugExpressionEvaluator::GetMethodProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluator::GetMethodProperty"
helpviewer_keywords: 
  - "Метод IDebugExpressionEvaluator::GetMethodProperty"
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionEvaluator::GetMethodProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод возвращает объект свойства, содержащего локальные переменные, аргументы и другие свойства метода.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetMethodProperty(   
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BOOL                  fIncludeHiddenLocals,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```c#  
int GetMethodProperty(  
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   int                  fIncludeHiddenLocals,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### Параметры  
 `pSymbolProvider`  
 \[in\] поставщик символа, который требуется использовать, выраженное как [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) объект.  
  
 `pAddress`  
 \[in\] адрес в коде, выраженном как [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) объект, то должен быть разрешен до ближайшего, содержащий функции.  
  
 `pBinder`  
 \[in\] связыватель использовать, выраженное как [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) объект.  
  
 `fIncludeHiddenLocals`  
 \[in\] ненулевое значение \(`TRUE`\) означает включить скрытые локальные переменные. ноль \(`FALSE`выйти за пределы скрыть локальные переменные\) означает  
  
 `ppProperty`  
 \[out\] возвращает IDebugProperty2 объект, представляющий метод.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Скрытые переменные, локальные переменные обычно создаются компилятором.  
  
## См. также  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)