---
title: "IDebugProgram2::EnumCodePaths | Microsoft Docs"
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
  - "IDebugProgram2::EnumCodePaths"
helpviewer_keywords: 
  - "IDebugProgram2::EnumCodePaths"
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::EnumCodePaths
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Извлекает список путей кода для заданной позиции в файле источника.  
  
## Синтаксис  
  
```cpp#  
HRESULT EnumCodePaths(   
   LPCOLESTR            pszHint,  
   IDebugCodeContext2*  pStart,  
   IDebugStackFrame2*   pFrame,  
   BOOL                 fSource,  
   IEnumCodePaths2**    ppEnum,  
   IDebugCodeContext2** ppSafety  
);  
```  
  
```c#  
int EnumCodePaths(   
   string                 pszHint,  
   IDebugCodeContext2     pStart,  
   IDebugStackFrame2      pFrame,  
   Int                    fSource,  
   out IEnumCodePaths2    ppEnum,  
   out IDebugCodeContext2 ppSafety  
);  
```  
  
#### Параметры  
 `pszHint`  
 \[in\] машинное слово под курсором в **Источник** OR  **Дизассемблированный код** представление в интегрированной среде разработки.  
  
 `pStart`  
 \[in\] IDebugCodeContext2 объект, представляющий текущий контекст кода.  
  
 `pFrame`  
 \[in\] [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) объект, представляющий кадр стека, связанный с текущей точкой останова.  
  
 `fSource`  
 \[in\] ненулевое значение \(`TRUE`если в\)  **Источник** представление или нуль \(`FALSE`если в\)  **Дизассемблированный код** представление.  
  
 `ppEnum`  
 \[out\] возвращает [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) объект, содержащий список путей кода.  
  
 `ppSafety`  
 \[out\] возвращает IDebugCodeContext2 объект, представляющий контекст дополнительного кода для быть установлены в качестве точки останова в случае, если выбранный путь кода пропущен.  Это может произойти в случае закороченного логического выражения, например.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Путь к коду описываются имя метода или функции, вызванный для доступа к текущему моменту выполнения программы.  Список путей кода представляет собой стек вызовов.  
  
## См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)