---
title: "Метод IJsDebugBreakPoint::GetDocumentPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebugBreakPoint.GetDocumentPosition
apilocation: jscript9diag.dll
ms.assetid: 886df8ba-a59a-48a7-87f2-3b669e71528f
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод IJsDebugBreakPoint::GetDocumentPosition
Возвращает позицию выписки, точка останова был привязан.  
  
## Синтаксис  
  
```  
HRESULT GetDocumentPosition(  
   UINT64 *pDocumentId,  
   DWORD *pCharacterOffset,  
   DWORD *pStatementCharCount  
);  
```  
  
#### Параметры  
 `pDocumentId`  
 \[out\] Уникальный идентификатор исходного документа \(указатель на IDebugDocumentText\).  
  
 `pCharacterOffset`  
 \[out\] Отсчитываемое от нуля смещение символа от начала скрипта.  
  
 `pStatementCharCount`  
 \[out\] Длина текущей инструкции, которая начинается с \*pCharacterOffset, в знаках.  
  
## Возвращаемое значение  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Интерфейс IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)