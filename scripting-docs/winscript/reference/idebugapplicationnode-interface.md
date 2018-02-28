---
title: "Интерфейс IDebugApplicationNode | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode interface
ms.assetid: 30be3a97-8191-45ac-8706-3f7056c163d6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 110e04d1c990f1b22f9740d8118a47f485dd041e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnode-interface"></a>Интерфейс IDebugApplicationNode
`IDebugApplicationNode` Интерфейс расширяет функциональность `IDebugDocumentProvider` интерфейс благодаря наличию контекста, в дереве проекта.  
  
 Помимо методов, наследуемых от `IDebugDocumentProvider`, `IDebugApplicationNode` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugApplicationNode::EnumChildren](../../winscript/reference/idebugapplicationnode-enumchildren.md)|Перечисляет дочерние узлы данного узла приложения.|  
|[IDebugApplicationNode::GetParent](../../winscript/reference/idebugapplicationnode-getparent.md)|Возвращает родительский узел данного узла приложения.|  
|[IDebugApplicationNode::SetDocumentProvider](../../winscript/reference/idebugapplicationnode-setdocumentprovider.md)|Задает поставщик документа для данного узла приложения.|  
|[IDebugApplicationNode::Close](../../winscript/reference/idebugapplicationnode-close.md)|В результате этого приложения освободить все ссылки и введите в неактивном состоянии.|  
|[IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)|Добавляет этот узел приложения в дерево указанный проект.|  
|[IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)|Удаляет данный узел приложения в дереве проекта.|