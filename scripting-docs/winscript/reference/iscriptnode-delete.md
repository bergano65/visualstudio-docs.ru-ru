---
title: "IScriptNode::Delete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.Delete
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::Delete"
ms.assetid: 6765ff80-a9a8-40a3-a669-7fcc284c87af
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptNode::Delete
Удаляет это дерево объектов.  
  
## Синтаксис  
  
```  
HRESULT Delete();  
```  
  
#### Параметры  
 Метод не принимает параметры.  
  
## Возвращаемое значение  
 Объект `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 После того, как метод `Delete` вызвать метод [IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md) должен указать, что узел скрипта не активен.  
  
## См. также  
 [Интерфейс IScriptNode](../../winscript/reference/iscriptnode-interface.md)