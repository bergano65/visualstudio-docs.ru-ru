---
title: 'Идебугаппликатионнодивентс:: Онремовечилд | Документация Майкрософт'
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
ms.openlocfilehash: f0ff7b28f14c26029d64197ba919cc97c90a856c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574667"
---
# <a name="idebugapplicationnodeeventsonremovechild"></a>IDebugApplicationNodeEvents::onRemoveChild
Обрабатывает событие при удалении дочернего узла из объекта узла приложения отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT onRemoveChild(  
   IDebugApplicationNode*  prddpChild  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `prddpChild`  
 окне Узел дочернего приложения, который был удален.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод обрабатывает событие при удалении дочернего узла из объекта узла приложения отладки.  
  
 Разработчики `IDebugApplicationNode`ного интерфейса вызывают это событие.  
  
## <a name="see-also"></a>См. также:  
   [интерфейса идебугаппликатионнодивентс](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
 [Идебугаппликатионнодивентс:: онаддчилд](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)   
 [Интерфейс IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)