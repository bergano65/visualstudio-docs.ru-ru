---
title: "IDispError::GetNext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetNext
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetNext"
ms.assetid: 3e5267f8-ba62-41c3-bd3e-eced2ad85e8e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetNext
Извлекает следующий объект `IDispError`.  
  
## Синтаксис  
  
```  
HRESULT GetNext(  
   IDispError**  ppde  
);  
```  
  
#### Параметры  
 `ppde`  
 \[out\] определяет следующий объект `IDispError`.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод извлекает следующий объект `IDispError`.  Если это последний объект `IDispError`, то получения этого метода АННУЛИРУЮТ.  
  
> [!NOTE]
>  Этот метод не реализован.  
  
## См. также  
 [Интерфейс IDispError](../../winscript/reference/idisperror-interface.md)