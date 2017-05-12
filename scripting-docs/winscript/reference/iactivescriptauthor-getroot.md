---
title: "IActiveScriptAuthor::GetRoot | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetRoot
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetRoot"
ms.assetid: 8e55a0c0-dd35-43d5-bf6f-e2f59c1e88d1
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptAuthor::GetRoot
Возвращает корневой элемент дерева `IScriptNode` скрипта автора.  
  
## Синтаксис  
  
```  
HRESULT GetRoot(  
   IScriptNode        **ppsp  
);  
```  
  
#### Параметры  
 `ppsp`  
 \[out\] адрес переменной, которая получает указатель на интерфейс `IScriptNode` корневого узла.  
  
## Возвращаемое значение  
 Объект `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
  
## См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [Интерфейс IScriptNode](../../winscript/reference/iscriptnode-interface.md)