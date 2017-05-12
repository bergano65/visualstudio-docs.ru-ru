---
title: "IDebugDocumentText::GetContextOfPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetContextOfPosition
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetContextOfPosition"
ms.assetid: 86560853-d9b1-499a-a1b5-ea06aa1f1f5c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetContextOfPosition
Создает объект контекста документа, соответствующий указанному диапазону позиции символа.  
  
## Синтаксис  
  
```  
HRESULT GetContextOfPosition(  
   ULONG                    cCharacterPosition,  
   ULONG                    cNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### Параметры  
 `cCharacterPosition`  
 \[in\] начальное положение диапазона позиции символа.  
  
 `cNumChars`  
 \[in\] количество символов в диапазоне.  
  
 `ppsc`  
 \[out\] объект контекста документа, соответствующий указанному диапазону позиции символа.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод создает объект контекста документа, соответствующий указанному диапазону позиции символа.  
  
## См. также  
 [Интерфейс IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)