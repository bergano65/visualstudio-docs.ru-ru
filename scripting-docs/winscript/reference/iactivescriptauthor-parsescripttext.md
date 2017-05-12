---
title: "IActiveScriptAuthor::ParseScriptText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.ParseScriptText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::ParseScriptText"
ms.assetid: ebe212e8-6789-423d-ad22-92be984dc7ad
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthor::ParseScriptText
Анализирует текст скрипта, добавить текст к скрипту создание обработчика и создает объект `IScriptEntry`, соответствующий блок скрипта.  
  
## Синтаксис  
  
```  
HRESULT ParseScriptText(  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### Параметры  
 `pszCode`  
 \[in\] текст скрипта, который необходимо проанализировать.  
  
 `pszItemName`  
 \[in\] адрес буфера, содержащий имя элемента, связанный с блоком скрипта.  
  
 `pszDelimiter`  
 \[in\] адрес разделителя элемент \- скрипт\- блока.  При `pszCode` анализироватьо из потока текста, основное приложение обычно использует разделитель как одинарных кавычек \(2\), чтобы обнаружить конец блока скрипта.  Установите этот параметр в значение null, если разделитель, чтобы указать конец блока скрипта.  
  
 `dwCookie`  
 \[in\] приложение\- указанное значение, сопоставитьо с новым объектом `IScriptEntry`.  
  
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