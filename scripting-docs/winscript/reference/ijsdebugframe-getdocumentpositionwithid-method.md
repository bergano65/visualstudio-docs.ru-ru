---
title: "Метод IJsDebugFrame::GetDocumentPositionWithId | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetDocumentPositionWithId
apilocation: jscript9diag.dll
ms.assetid: 48f8eb26-8ae4-4d5c-bd94-796023b03bcb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод IJsDebugFrame::GetDocumentPositionWithId
Возвращает текущее положение этого кадра стека в пределах пользовательского документа.  
  
## Синтаксис  
  
```  
HRESULT GetDocumentPositionWithId(  
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
 [Интерфейс IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)