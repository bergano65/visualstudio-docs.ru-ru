---
title: "IDebugDocumentHost::GetFileName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.GetFileName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::GetFileName"
ms.assetid: b814a848-8a3d-468d-9282-c5c0354b22a1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::GetFileName
Возвращает имя документа без информации пути.  
  
## Синтаксис  
  
```  
HRESULT GetFileName(  
   BSTR*  pbstrShortName  
);  
```  
  
#### Параметры  
 `pbstrShortName`  
 \[out\] строка, содержащая a короткое имя документа.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод возвращает короткое имя документа без информации пути.  Короткое имя обычно используется в тех случаях, например диалоговое окно **\*\*\* сохранить как… \*\*\***.  
  
## См. также  
 [Интерфейс IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)