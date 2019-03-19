---
title: IDebugApplicationNodeEvents::onRemoveChild | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onRemoveChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onRemoveChild
ms.assetid: 2e025d29-b8c0-4793-a2d3-c20d548d6386
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e59624e5ec6659e0fea3d55fdaddf7949eac18f
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147934"
---
# <a name="idebugapplicationnodeeventsonremovechild"></a>IDebugApplicationNodeEvents::onRemoveChild
Обрабатывает событие, когда дочерний узел удаляется из объект узла отладки приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT onRemoveChild(  
   IDebugApplicationNode*  prddpChild  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `prddpChild`  
 [in] Дочерний узел приложения, который был удален.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод обрабатывает событие, когда дочерний узел удаляется из объект узла отладки приложения.  
  
 Объекты, реализующие `IDebugApplicationNode` интерфейс вызова этого события.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)   
 [Интерфейс IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)