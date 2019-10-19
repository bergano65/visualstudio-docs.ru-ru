---
title: Интерфейс Искриптноде | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 38ab73ddb1bd924035cb6ba61d26e65f16f53eed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577515"
---
# <a name="iscriptnode-interface"></a>Интерфейс IScriptNode
Объект, реализующий интерфейс `IScriptNode`, представляет веб-страницу.  
  
 В дополнение к методам, унаследованным от `IUnknown`, интерфейс `IScriptNode` предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|Указывает, активен ли объект.|  
|[IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|Добавляет дочерний экземпляр `IScriptEntry`.|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|Добавляет скриптлет в качестве дочернего экземпляра `IScriptNode`.|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|Удаляет дерево объектов.|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|Возвращает дочерний элемент, расположенный по указанному индексу в узле.|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|Возвращает определяемое приложением значение, которое используется для связывания скриптлет с объектом узла.|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|Возвращает индекс объекта в дочернем списке родительского элемента.|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|Возвращает язык скрипта, используемый текущим узлом скрипта.|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|Возвращает количество дочерних узлов объекта `IScriptNode`.|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|Возвращает объект `IScriptNode`, являющийся родительским для объекта.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы для создания активных скриптов](../../winscript/reference/active-script-authoring-interfaces.md)