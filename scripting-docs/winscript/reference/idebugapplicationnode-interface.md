---
title: "Интерфейс IDebugApplicationNode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode — интерфейс"
ms.assetid: 30be3a97-8191-45ac-8706-3f7056c163d6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Интерфейс IDebugApplicationNode
Интерфейс `IDebugApplicationNode` расширяющий функциональность интерфейса `IDebugDocumentProvider`, предоставляя контекста внутри дерева проекта.  
  
 В дополнение к методам, наследуемым от интерфейса `IDebugDocumentProvider`, интерфейс `IDebugApplicationNode` предоставляет следующие методы.  
  
## Методы в том порядке Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugApplicationNode::EnumChildren](../../winscript/reference/idebugapplicationnode-enumchildren.md)|Перечисляет дочерние узлы данного узла приложения.|  
|[IDebugApplicationNode::GetParent](../../winscript/reference/idebugapplicationnode-getparent.md)|Получает родительский узел данного узла приложения.|  
|[IDebugApplicationNode::SetDocumentProvider](../../winscript/reference/idebugapplicationnode-setdocumentprovider.md)|Задает поставщика документа для данного узла приложения.|  
|[IDebugApplicationNode::Close](../../winscript/reference/idebugapplicationnode-close.md)|Вызывает это приложение освободить все ссылки и выполнить вход неактивного состояние.|  
|[IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)|Добавляет этот узел приложения в указанное дерево проекта.|  
|[IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)|Удаляет данный узел приложения из дерева проекта.|