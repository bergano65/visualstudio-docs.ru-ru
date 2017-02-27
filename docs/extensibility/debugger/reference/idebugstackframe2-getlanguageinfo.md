---
title: "IDebugStackFrame2::GetLanguageInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2::GetLanguageInfo"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetLanguageInfo"
ms.assetid: 0e12fd92-f155-46a7-8272-cda279388cfb
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugStackFrame2::GetLanguageInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает язык, связанный с данным кадром стека.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetLanguageInfo (   
   BSTR* pbstrLanguage,  
   GUID* pguidLanguage  
);  
```  
  
```c#  
int GetLanguageInfo (   
   ref string pbstrLanguage,  
   ref Guid   pguidLanguage  
);  
```  
  
#### Параметры  
 `pbstrLanguage`  
 \[out\] возвращает имя языка, который реализует метод, связанный с данным кадром стека.  
  
 `pguidLanguage`  
 \[out\] возвращает `GUID` языка.  Для [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] языки, например, следующее может возвратить:  
  
-   `guidVBScriptLang`  
  
-   `guidJScriptLang`  
  
-   `guidCPPLang`  
  
-   `guidVBLang`  
  
-   `guidSQLLang`  
  
-   `guidScriptLang`  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)