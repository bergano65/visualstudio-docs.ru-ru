---
title: "IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProcessSecurity::QueryCanSafelyAttach"
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugProcessSecurity::QueryCanSafelyAttach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод позволяет поставщику порта для отображения предупреждения, прежде чем пользователю опасному вложение в процесс.  
  
## Синтаксис  
  
```cpp#  
HRESULT QueryCanSafelyAttach();  
```  
  
```c#  
int QueryCanSafelyAttach();  
```  
  
## Возвращаемое значение  
 Возвращаемые значения следующим образом:  
  
-   `S_OK`. Вложение для обработки является безопасным и никакое диалоговое окно предупреждения не отображается.  
  
-   `S_FALSE`. Вложение может быть проблемой, безопасности и отображается диалоговое окно с предупреждением.  
  
-   `FAILURE`. Вложение для обработки fail.  
  
## См. также  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)