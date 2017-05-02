---
title: "Интерфейс IScriptNode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IScriptNode — интерфейс"
ms.assetid: cfa76c4a-6543-48e8-a946-d212cd0bf934
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Интерфейс IScriptNode
Объект, средства интерфейс `IScriptNode` представляют страницу.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IScriptNode` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|Указывает, является ли объект еще активен.|  
|[IScriptNode::CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|Добавляет экземпляр дочернего элемента `IScriptEntry`.|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|Добавляет сценарий, как экземпляр дочернего элемента `IScriptNode`.|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|Удаляет дерево объектов.|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|Возвращает дочерний элемент, который в указанном индексе в узле.|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|Возвращает приложение\- указанное значение, которое используется для связывания сценарий с объектом основного приложения.|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|Возвращает индекс объекта в списке дочернего элемента родительского элемента.|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|Возвращает язык сценария, используемый текущим узлом скрипта.|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|Возвращает число дочерних узлов объекта `IScriptNode`.|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|Возвращает объект `IScriptNode`, являющийся родительским для объекта.|  
  
## См. также  
 [Интерфейсы для создания активных скриптов](../../winscript/reference/active-script-authoring-interfaces.md)