---
title: "ISimpleConnectionPoint::Unadvise | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.Unadvise
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::Unadvise"
ms.assetid: eae06a58-ed42-4839-aad4-14420b15343f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::Unadvise
Завершает вспомогательное подключение, установленное ранее при помощи `ISimpleConnectionPoint::Advise`.  
  
## Синтаксис  
  
```  
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### Параметры  
 `dwCookie`  
 \[in\] маркер соединения завершения, возвращенный `ISimpleConnectionPoint::Advise`.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Вспомогательное соединение завершитьо, если точка подключения вызывает метод `Release` указателя, который был сохранен для подключения во время выполнения метода `ISimpleConnectionPoint::Advise`.  Этот вызов обращает `AddRef`, выполненной во время `ISimpleConnectionPoint::Advise`, если точка подключения вызывает `QueryInterface` консультативного приемников.  
  
## См. также  
 [Интерфейс ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)