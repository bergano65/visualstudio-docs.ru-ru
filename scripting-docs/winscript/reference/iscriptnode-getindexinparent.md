---
title: "IScriptNode::GetIndexInParent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetIndexInParent
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetIndexInParent"
ms.assetid: 521c1ca1-2d27-4344-bf3b-d8b53132b648
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IScriptNode::GetIndexInParent
Возвращает индекс объекта в списке дочернего элемента родительского элемента.  
  
## Синтаксис  
  
```  
HRESULT GetIndexInParent(  
   ULONG              pisn,  
);  
```  
  
#### Параметры  
 `pisn`  
 \[out\] возвращает индекс объекта в списке дочернего элемента родительского элемента.  
  
 Если этот метод вызывается объектом, `IScriptNode`, представляющий страницу, return 0 этого параметра.  
  
## Возвращаемое значение  
 Объект `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
  
## См. также  
 [Интерфейс IScriptNode](../../winscript/reference/iscriptnode-interface.md)