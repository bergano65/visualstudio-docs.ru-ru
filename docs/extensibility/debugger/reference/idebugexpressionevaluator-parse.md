---
title: "IDebugExpressionEvaluator::Parse | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluator::Parse"
helpviewer_keywords: 
  - "Метод IDebugExpressionEvaluator::Parse"
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugExpressionEvaluator::Parse
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод преобразует строку выражения в анализированному выражению.  
  
## Синтаксис  
  
```cpp#  
HRESULT Parse(   
   LPCOLESTR                upstrExpression,  
   PARSEFLAGS               dwFlags,  
   UINT                     nRadix,  
   BSTR*                    pbstrError,  
   UINT*                    pichError,  
   IDebugParsedExpression** ppParsedExpression  
);  
```  
  
```c#  
int Parse(  
   string                     upstrExpression,   
   enum_PARSEFLAGS            dwFlags,   
   uint                       nRadix,   
   out string                 pbstrError,   
   out uint                   pichError,   
   out IDebugParsedExpression ppParsedExpression  
);  
```  
  
#### Параметры  
 `upstrExpression`  
 \[in\] строка выражения, которое необходимо проанализировать.  
  
 `dwFlags`  
 \[in\] коллекция [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) константы, определяющие, как выражение анализируется.  
  
 `nRadix`  
 \[in\] корневой каталог, используемый для интерпретации любое числовое сведения.  
  
 `pbstrError`  
 \[out\] возвращает ошибку в виде удобочитаемого текста.  
  
 `pichError`  
 \[out\] возвращает позицию знака начала ошибки в строке выражения.  
  
 `ppParsedExpression`  
 \[out\] возвращает прошедшее синтаксический анализ выражения в [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) объект.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Этот метод создает проанализированное выражение, не фактическое значение.  Проанализированное выражение готово должен вычисляться, т е преобразовать в значение.  
  
## См. также  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)