---
title: "IDispError::QueryErrorInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.QueryErrorInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::QueryErrorInfo"
ms.assetid: e7e71a14-77e2-4331-9ffc-1dace041fa84
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::QueryErrorInfo
Извлекает указанный тип сведений об ошибке.  
  
## Синтаксис  
  
```  
HRESULT QueryErrorInfo(  
   GUID  guidErrorType,  
   IDispError**  ppde  
);  
```  
  
#### Параметры  
 `guidErrorType`  
 \[in\] идентификатор GUID, определяющий тип ошибки.  
  
 `ppde`  
 \[out\] задает объект IDispError.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Метод `QueryErrorInfo` извлекает указанный тип сведений об ошибке.  
  
> [!NOTE]
>  Этот метод не реализован.  
  
## См. также  
 [Интерфейс IDispError](../../winscript/reference/idisperror-interface.md)