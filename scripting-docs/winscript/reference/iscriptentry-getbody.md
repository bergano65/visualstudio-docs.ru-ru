---
title: "IScriptEntry::GetBody | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetBody
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetBody"
ms.assetid: 419c8c11-a1f8-4b97-ab00-e8af2b2f9bfc
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetBody
Возвращает текст, который соответствует тексту сообщения блока скрипта `IScriptEntry`, функции или блока скрипта.  
  
## Синтаксис  
  
```  
HRESULT GetBody(  
   BSTR               *pbstr  
);  
```  
  
#### Параметры  
 `pbstr`  
 \[out\] текст, в теле одного из следующих условий:  
  
-   Блок скрипта `IScriptEntry`  
  
-   Функция `IScriptEntry` в блоке функции  
  
-   Обработчик скриптов `IScriptEntry`  
  
## Возвращаемое значение  
 Объект `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
  
## См. также  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)