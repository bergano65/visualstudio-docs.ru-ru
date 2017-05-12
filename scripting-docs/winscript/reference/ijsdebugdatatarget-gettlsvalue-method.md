---
title: "Метод IJsDebugDataTarget::GetTlsValue | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.GetTlsValue
apilocation: jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод IJsDebugDataTarget::GetTlsValue
Для отлаживаемого потока извлекает значение из ячейки локальной памяти потока \(TLS\) для указанного индекса TLS.  
  
## Синтаксис  
  
```  
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### Параметры  
 `threadId`  
 \[in\] Поток для чтения, выполняемый в целевом процессе.  
  
 `tlsIndex`  
 \[in\] Индекс TLS, который был выделен, когда целевой процесс вызвал функцию TlsAlloc.  
  
 `pValue`  
 \[out\] Значение размера указателя, которое было сохранено в слоте TLS потока.  Если целевой поток 32\-разрядный, верхние 32 бита этого значения будут равны нулю.  
  
## Возвращаемое значение  
  
## Заметки  
 Каждый поток процесса имеет собственную ячейку для каждого индекса TLS.  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)