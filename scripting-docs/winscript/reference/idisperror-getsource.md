---
title: "IDispError::GetSource | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetSource
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetSource"
ms.assetid: 20def54c-a67c-4102-babf-6f0704e5fc5c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetSource
Возвращает идентификатор progid зависящим от языка для класса или приложения, подняли ошибку.  
  
## Синтаксис  
  
```  
HRESULT GetSource(  
   BSTR*  pbstrSource  
);  
```  
  
#### Параметры  
 `pbstrSource`  
 \[out\] зашнуруйте, содержащий идентификатор progid, в форме `progname.objectname`.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод используется для определения класса или приложение, в котором возникло исключение.  Идентификатор progid может быть возвращен на языке, указанном кодом языка \(код языка\) предоставленным во время вызова.  
  
> [!NOTE]
>  Этот метод не реализован.  
  
## См. также  
 [Интерфейс IDispError](../../winscript/reference/idisperror-interface.md)