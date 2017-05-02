---
title: "IActiveScriptAuthor::GetEventHandler | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetEventHandler
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetEventHandler"
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptAuthor::GetEventHandler
Возвращает скрипт, который имеет указанные атрибуты.  
  
## Синтаксис  
  
```  
HRESULT GetEventHandler(  
   IDispatch          *pdisp,  
   LPCOLESTR          pszItem,  
   LPCOLESTR          pszSubItem,  
   LPCOLESTR          pszEvent,  
   IScriptEntry       **ppse  
);  
```  
  
#### Параметры  
 `pdisp`  
 \[in\] объект `IDispatch`, соответствующий `NamedItem`, к которому сценарий вложить.  
  
 `pszItem`  
 \[in\] адрес буфера верхнего уровня идентификатора полного имени скрипта в узле.  
  
 `pszSubItem`  
 \[in\] адрес буфера идентификатора втор\- уровня полного имени скрипта в узле.  Задайте значение null, если имя имеет только один уровень.  
  
 `pszEvent`  
 \[in\] адрес буфера, содержащий имя события.  Скрипт обработчика событий для этого события.  
  
 `ppse`  
 \[out\] адрес переменной, которая получает указатель на интерфейс `IScriptEntry` скрипта, который имеет указанные атрибуты.  
  
## Возвращаемое значение  
 Объект `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
  
## См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)