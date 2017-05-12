---
title: "IActiveScriptAuthor::AddScriptlet | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.AddScriptlet
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::AddScriptlet"
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptAuthor::AddScriptlet
Добавляет сценарий кода как дочерний элемент корневого уровня объекта `IScriptNode`.  В основном приложении полное имя скрипта разрешитьо иметь только 2 уровня.  
  
## Синтаксис  
  
```  
HRESULT AddScriptlet(  
   LPCOLESTR pszDefaultName,  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszSubItemName,  
   LPCOLESTR pszEventName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### Параметры  
 `pszDefaultName`  
 \[in\] адрес имя по умолчанию, связанное со скриптом.  
  
 `pszCode`  
 \[in\] адрес текст сценария.  
  
 `pszItemName`  
 \[in\] адрес буфера верхнего уровня идентификатора полного имени скрипта в узле.  
  
 `pszSubItemName`  
 \[in\] адрес буфера идентификатора втор\- уровня полного имени скрипта в узле.  Задайте значение null, если имя имеет только один уровень.  
  
 `pszEventName`  
 \[in\] адрес буфера, содержащий имя события, для которого скрипт обработчика событий.  
  
 `pszDelimiter`  
 \[in\] адрес разделителя элемент \- скрипт\- блока.  При `pszCode` анализироватьо из потока текста, основное приложение обычно использует разделитель как одинарных кавычек \(2\), чтобы обнаружить конец блока скрипта.  Установите этот параметр в значение null, если разделитель не отмечает конец блока скрипта.  
  
 `dwCookie`  
 \[in\] приложение\- указанное значение, которое используется для связывания сценарий с объектом основного приложения.  
  
 `dwFlags`  
 \[in\] Не используется.  
  
## Возвращаемое значение  
 Объект `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
  
## См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)