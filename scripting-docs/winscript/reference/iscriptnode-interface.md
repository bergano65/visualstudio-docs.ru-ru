---
title: Интерфейс IScriptNode | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptNode interface
ms.assetid: cfa76c4a-6543-48e8-a946-d212cd0bf934
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 788be3fe9cb5ba529e3d1ca653d4f0f5c35b5932
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24733784"
---
# <a name="iscriptnode-interface"></a>Интерфейс IScriptNode
Объект, реализующий интерфейс `IScriptNode` интерфейс представляет веб-страницы.  
  
 Помимо методов, наследуемых от `IUnknown`, `IScriptNode` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|Указывает, является ли объект все еще активны.|  
|[IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|Добавляет дочерний экземпляр `IScriptEntry`.|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|Добавляет в качестве экземпляра дочернего пользователи `IScriptNode`.|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|Удаляет дерева объектов.|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|Возвращает дочерний элемент по указанному индексу в узле.|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|Возвращает значение, определяемые приложением, которое используется для связи с объектом узла пользователи.|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|Возвращает индекс объекта в списке дочерних элементов родительского элемента.|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|Возвращает язык сценариев, используемый узлом скрипта.|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|Возвращает количество дочерних узлов `IScriptNode` объекта.|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|Возвращает `IScriptNode` объект, являющийся родительским для объекта.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы для создания активных скриптов](../../winscript/reference/active-script-authoring-interfaces.md)