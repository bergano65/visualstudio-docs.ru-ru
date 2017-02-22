---
title: "IDebugModule2::ReloadSymbols_Deprecated | Microsoft Docs"
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
  - "IDebugModule2::ReloadSymbols"
helpviewer_keywords: 
  - "Метод IDebugModule2::ReloadSymbols"
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugModule2::ReloadSymbols_Deprecated
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

УСТАРЕЛ.  НЕ ИСПОЛЬЗУЙТЕ.  Перезагрузить символов для этого модуля.  
  
## Синтаксис  
  
```cpp#  
HRESULT ReloadSymbols(   
   LPCOLESTR pszUrlToSymbols,  
   BSTR*     pbstrDebugMessage  
);  
```  
  
```c#  
int ReloadSymbols(   
   string     pszUrlToSymbols,  
   out string pbstrDebugMessage  
);  
```  
  
#### Параметры  
 `pszUrlToSymbols`  
 \[in\] путь в хранилище символов.  
  
 `pbstrDebugMessage`  
 \[out\] возвращает информационное сообщение, например состояние или сообщение об ошибке, в котором отображаются справа от имени модуля в окне модули.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  Отладчик должен всегда возвращать `E_FAIL`.  
  
## Заметки  
 Этот метод больше не поддерживается.  Реализуйте [LoadSymbols](../Topic/IDebugModule3::LoadSymbols.md) вместо этого метод.  
  
## См. также  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [LoadSymbols](../Topic/IDebugModule3::LoadSymbols.md)