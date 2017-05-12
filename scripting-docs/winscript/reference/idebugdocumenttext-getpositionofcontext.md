---
title: "IDebugDocumentText::GetPositionOfContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetPositionOfContext
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetPositionOfContext"
ms.assetid: 90fec730-c3fb-45fb-92ef-05ecc90dca38
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetPositionOfContext
Возвращает диапазон позиции символа, соответствующий контексту документа.  
  
## Синтаксис  
  
```  
HRESULT GetPositionOfContext(  
   IDebugDocumentContext*  psc,  
   ULONG*                  pcCharacterPosition,  
   ULONG*                  cNumChars  
);  
```  
  
#### Параметры  
 `psc`  
 \[in\] объект контекста документа.  
  
 `pcCharacterPosition`  
 \[out\] начальное положение диапазона позиции символа.  
  
 `cNumChars`  
 \[out\] количество символов в диапазоне.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Контекст рисования, на который этот метод необходимо связать с данным документом.  
  
## См. также  
 [Интерфейс IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)