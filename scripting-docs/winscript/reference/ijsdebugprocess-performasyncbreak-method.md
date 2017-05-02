---
title: "Метод IJsDebugProcess::PerformAsyncBreak | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugProcess.PerformAsyncBreak
apilocation: jscript9diag.dll
ms.assetid: 2a6ee369-ea99-4332-8521-a1741ccb6292
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод IJsDebugProcess::PerformAsyncBreak
Помещает обработчик скриптов в режим приостановки выполнения вызывает его прерывание в следующей инструкции скрипта.  
  
## Синтаксис  
  
```  
HRESULT PerformAsyncBreak(  
   DWORD threadId  
);  
```  
  
#### Параметры  
 `threadId`  
 \[in\] Идентификатор потока.  
  
## Возвращаемое значение  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Интерфейс IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)