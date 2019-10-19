---
title: 'Идебугаппликатионнодивентс:: Онаддчилд | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onAddChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onAddChild
ms.assetid: 59ce33cf-1843-4b03-98a2-34859d3023f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 052fe47f1ddf2d20e7486a95a9dd79bc388f7ebc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574710"
---
# <a name="idebugapplicationnodeeventsonaddchild"></a>IDebugApplicationNodeEvents::onAddChild
Обрабатывает событие при добавлении дочернего узла в объект узла приложения отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT onAddChild(  
   IDebugApplicationNode*  prddpChild  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `prddpChild`  
 окне Добавленный узел дочернего приложения отладки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод обрабатывает событие при добавлении дочернего узла в объект узла приложения отладки.  
  
 Разработчики `IDebugApplicationNode`ного интерфейса вызывают это событие  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса идебугаппликатионнодивентс](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
 [Идебугаппликатионнодивентс:: онремовечилд](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)    
 [Интерфейс IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)