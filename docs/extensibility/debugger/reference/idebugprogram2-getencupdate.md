---
title: "IDebugProgram2::GetENCUpdate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetENCUpdate"
helpviewer_keywords: 
  - "IDebugProgram2::GetENCUpdate"
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugProgram2::GetENCUpdate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод возвращает правку и продолжить обновление \(ENCL\) для этой программы.  Всегда возвращает пользовательский обработчик отладки `E_NOTIMPL`.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetENCUpdate(   
   IUnknown** ppUpdate  
);  
```  
  
```c#  
int GetENCUpdate(  
   out object ppUpdate  
);  
```  
  
#### Параметры  
 `ppUpdate`  
 \[out\] возвращает внутренний интерфейс, который может быть использован для обновления этой программы.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
> [!NOTE]
>  Пользовательский обработчик отладки должны всегда возвращать `E_NOTIMPL`.  
  
## См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)