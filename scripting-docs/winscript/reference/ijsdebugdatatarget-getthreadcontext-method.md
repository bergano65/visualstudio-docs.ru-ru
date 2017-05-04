---
title: "Метод IJsDebugDataTarget::GetThreadContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.GetThreadContext
apilocation: jscript9diag.dll
ms.assetid: faf2a689-6c49-4a7d-b5a6-2b323e2257a7
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод IJsDebugDataTarget::GetThreadContext
Возвращает контекст для данного потока.  
  
## Синтаксис  
  
```  
HRESULT GetThreadContext(  
   DWORD threadId,  
   ULONG32 contextFlags,  
   ULONG32 contextSize,  
   void *pContext  
);  
```  
  
#### Параметры  
 `threadId`  
 \[in\] Поток, выполняемый в целевом процессе.  
  
 `contextFlags`  
 \[in\] Задает флаги контекста.  Это то же поле ContextFlags КОНТЕКСТА \(дополнительные сведения см. в разделе winnt.h, ищите CONTEXT\_ALL\).  
  
 `contextSize`  
 \[in\] Размер буфера, заданного pContext.  
  
 `pContext`  
 \[out\] Получает структуру CONTEXT, зависящую от платформы, в буфер, заданный pContext.  
  
## Возвращаемое значение  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)