---
title: "IActiveScriptAuthor::AddNamedItem | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.AddNamedItem
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::AddNamedItem"
ms.assetid: 951003b6-1c4a-4086-b7ce-2f128e007280
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# IActiveScriptAuthor::AddNamedItem
Добавляет имя элемента корень\- уровня к скрипту разработка пространство имен обработчика.  *Элемент корень\- уровня* объект, который может содержать свойства и методы, и может также содержать источник события.  
  
## Синтаксис  
  
```  
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### Параметры  
 `pszName`  
 \[in\] имя элемента, как доступна из скрипта.  Имя должно быть уникальным и постоянного.  
  
 `dwFlags`  
 \[in\] флаги, которые сопоставитьы с именованным элементом.  Может быть сочетанием следующих значений:  
  
|Константа|Значение|Описание|  
|---------------|--------------|--------------|  
|SCRIPTITEM\_ISVISIBLE|0x00000002|Указывает на то, что имя элемента содержатся в пространстве имен скрипта.  Это позволяет получить доступ к свойствам, методам и событиям элемента.<br /><br /> По соглашению свойства элементов включают дочерние элементы элемента.  Поэтому все свойства дочерних объектов и методы \(и их потомки, рекурсивно\) доступны.|  
|SCRIPTITEM\_ISSOURCE|0x00000004|Указывает события источника элемента, что скрипт может содержать обработчики событий скрипта.|  
|SCRIPTITEM\_GLOBALMEMBERS|0x00000008|Указывает, что элемент коллекцию глобальных свойств и методов, сопоставитьы со скриптом.  Его члены разрабатываются как глобальные переменные и методы.|  
|SCRIPTITEM\_ISPERSISTENT|0x00000040|Указывает, что элемент должен быть сохранен, если скрипт создание обработчика сохранить.|  
|SCRIPTITEM\_CODEONLY|0x00000200|Указывает, что именованный элемент представляющий объект кода \- только и не имеет участника создания.|  
|SCRIPTITEM\_NOCODE|0x00000400|Указывает, что именованный элемент просто добавляется имя и не имеющий никаких действий создания.|  
  
 `pdisp`  
 \[in\] `IDispatch` объекта `NamedItem`, который используется для сбора методы, свойства или источник события.  
  
## Возвращаемое значение  
 Объект `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
  
## См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)