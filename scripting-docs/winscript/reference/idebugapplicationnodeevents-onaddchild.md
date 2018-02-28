---
title: "IDebugApplicationNodeEvents::onAddChild | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onAddChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onAddChild
ms.assetid: 59ce33cf-1843-4b03-98a2-34859d3023f7
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3df872cd14b6d7fcd455371d1601b2a4082fb39a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnodeeventsonaddchild"></a>IDebugApplicationNodeEvents::onAddChild
Обрабатывает событие, когда дочерний узел добавляется в объект узла отладки приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT onAddChild(  
   IDebugApplicationNode*  prddpChild  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `prddpChild`  
 [in] Дочерний отладки приложения узел, который был добавлен.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод обрабатывает событие, когда дочерний узел добавляется в объект узла отладки приложения.  
  
 Объекты, реализующие `IDebugApplicationNode` интерфейс вызова этого события  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)   
 [Интерфейс IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)