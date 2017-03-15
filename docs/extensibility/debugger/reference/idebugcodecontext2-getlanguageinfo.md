---
title: "IDebugCodeContext2::GetLanguageInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCodeContext2::GetLanguageInfo"
helpviewer_keywords: 
  - "IDebugCodeContext2::GetLanguageInfo"
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugCodeContext2::GetLanguageInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Получает сведения о языке для этого контекста кода.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetLanguageInfo(   
   BSTR* pbstrLanguage,  
   GUID* pguidLanguage  
);  
```  
  
```c#  
int GetLanguageInfo(   
   ref string pbstrLanguage,  
   ref Guid pguidLanguage  
);  
```  
  
#### Параметры  
 `pbstrLanguage`  
 \[in, out\] возвращает строку, содержащую имя языка, например C\+\+ "."  
  
 `pguidLanguage`  
 \[in, out\] возвращает идентификатор GUID для языка контекста кода, например `guidCPPLang`.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Хотя бы один из параметров должен возвратить ненулевое значение.  
  
## См. также  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)