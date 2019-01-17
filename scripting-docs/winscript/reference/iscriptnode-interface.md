---
title: Интерфейс IScriptNode | Документация Майкрософт
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
ms.openlocfilehash: d8897d783f8a101b41dd7263061604fb1d82ec56
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344620"
---
# <a name="iscriptnode-interface"></a>Интерфейс IScriptNode
Объект, реализующий `IScriptNode` интерфейс представляет веб-страницы.  
  
 Помимо методов, наследуемых от `IUnknown`, `IScriptNode` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|Указывает, является ли объект все еще активна.|  
|[IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|Добавляет дочерний экземпляр `IScriptEntry`.|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|Добавляет в качестве дочернего экземпляра пользователи `IScriptNode`.|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|Удаляет дерева объектов.|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|Возвращает дочерний элемент, находящийся по указанному индексу в узле.|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|Возвращает значение, определяемые приложением, которое используется для связывания с объектом главного пользователи.|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|Возвращает индекс объекта в списке дочерних элементов родительского элемента.|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|Возвращает язык сценариев, используемый узлом текущего скрипта.|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|Возвращает количество дочерних узлов `IScriptNode` объекта.|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|Возвращает `IScriptNode` объект, являющийся родительским для объекта.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы для создания активных скриптов](../../winscript/reference/active-script-authoring-interfaces.md)