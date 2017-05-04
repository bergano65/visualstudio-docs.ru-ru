---
title: "IActiveScriptAuthor::GetLanguageFlags | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetLanguageFlags
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetLanguageFlags"
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# IActiveScriptAuthor::GetLanguageFlags
Возвращает сведения о языке.  
  
## Синтаксис  
  
```  
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### Параметры  
 `pgrfasa`  
 \[out\] флаги, которые содержат сведения о языке.  Может быть сочетанием следующих значений:  
  
|Константа|Значение|Описание|  
|---------------|--------------|--------------|  
|fasaPreferInternalHandler|0x0001|Язык обозревателем создание обработчика событий скрипта скриптом создания обработчика вместо приложения.|  
|fasaSupportInternalHandler|0x0002|Язык сценария поддерживает обработчики событий, созданные скриптом создания обработчика.|  
|fasaCaseSensitive|0x0004|Язык скрипта регистр.|  
  
## Возвращаемое значение  
 Объект `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Если скрипт создание обработчика управляет обработчики событий, приложение должно вызвать `CreateChildHandler` из объекта `IScriptEntry`.  Это создает объект `IScriptScriptlet`, соответствующий обработчик событий.  Обработчик также добавляет обработчик события для записи скрипта.  Обработчик событий пустая функция, которая содержит заданную подпись.  
  
 Если приложение управляет обработчики событий, оно должно вызвать `CreateChildHandler` из объекта `IScriptNode`, который представляет скрипт обработчика событий.  Это создает объект `IScriptScriptlet`, который связан с сценарием обработчика событий.  Приложение также необходимо добавить пустую функции в качестве обработчика событий в новый или существующий объект `IScriptEntry`.  
  
## См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)