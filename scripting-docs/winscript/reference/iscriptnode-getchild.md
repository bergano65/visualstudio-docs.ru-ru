---
title: "IScriptNode::GetChild | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetChild
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetChild"
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptNode::GetChild
Возвращает дочерний элемент, который в указанном индексе в узле.  
  
## Синтаксис  
  
```  
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### Параметры  
 `isn`  
 \[in\] индекс дочернего элемента в родительском элементе.  
  
 `ppsn`  
 \[out\] адрес переменной, которая получает указатель на интерфейс `IScriptNode` экземпляра дочернего элемента.  
  
 Для объектов `IScriptNode`, представляющие страницу, передачи этого параметра объект, который содержит блок скрипта.  
  
 Для объектов `IScriptEntry`, которые определяют блок скрипта, передачи этого параметра объект, задающий функцию.  
  
## Возвращаемое значение  
 Объект `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Для объектов `IScriptEntry`, определяющие объект функции и для объектов `IScriptScriptlet` этого метода завершается неудачей, так как нет записи дочернего элемента.  
  
## См. также  
 [Интерфейс IScriptNode](../../winscript/reference/iscriptnode-interface.md)