---
title: "ISimpleConnectionPoint::Advise | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.Advise
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::Advise"
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::Advise
Устанавливает связь между простой объект точки подключения и приемник клиента.  
  
## Синтаксис  
  
```  
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### Параметры  
 `pdisp`  
 \[in\] указатель на интерфейс `IDispatch` на клиенте советует приемник.  Приемник клиента получает исходящие вызовы от простой точки подключения.  
  
 `pdwCookie`  
 \[out\] указатель на возвращенный токену, уникально определяющий это соединение.  Вызывающая сторона использует этот токен позже для удаления соединения, передав его методу `ISimpleConnectionPoint::Unadvise`.  Если соединение не было установлено успешно, то это значение равно нулю.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод устанавливает связь между простой объект точки подключения и приемник клиента.  
  
## См. также  
 [Интерфейс ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)