---
title: "ISimpleConnectionPoint::DescribeEvents | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.DescribeEvents
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::DescribeEvents"
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::DescribeEvents
Возвращает идентификатор DISPID и имя каждого события в указанном диапазоне событий.  
  
## Синтаксис  
  
```  
HRESULT DescribeEvents(  
   ULONG    iEvent,  
   ULONG    cEvents,  
   DISPID*  prgid,  
   BSTR*    prgbstr,  
   ULONG*   pcEventsFetched  
);  
```  
  
#### Параметры  
 `iEvent`  
 \[in\] индекс первого события, который необходимо извлечь.  
  
 `cEvents`  
 \[in\] число событий, которые нужно получить.  
  
 `prgid`  
 \[out\] массив значений DISPID события.  
  
 `prgbstr`  
 \[out\] массив имен события.  
  
 `pcEventsFetched`  
 \[out\] фактическое количество выбранных событий.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
|`S_FALSE`|Несколько событий была поставлена не был доступен.  Недоступные события представлены с DISPID\_NULL BSTR и null.|  
|`E_INVALIDARG`|Элементы не могут быть получены.|  
  
## Заметки  
 Этот метод возвращает идентификатор DISPID и имя каждого события в указанном диапазоне событий.  
  
## См. также  
 [Интерфейс ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)