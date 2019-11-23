---
title: 'Идебугаппликатионнодивентс:: ondetach | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onDetach
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onDetach
ms.assetid: ef0cbe40-8c52-4bc9-bed0-9fc508abec6e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb1a33cbec8ef032c1c4fedba28ad4013e676f0d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574680"
---
# <a name="idebugapplicationnodeeventsondetach"></a>IDebugApplicationNodeEvents::onDetach
Обрабатывает событие, которое означает, что объект узла приложения отладки был отсоединен от родительского узла.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT onDetach();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод обрабатывает событие, которое означает, что объект узла приложения отладки был отсоединен от родительского узла.  
  
 Разработчики `IDebugApplicationNode`ного интерфейса вызывают это событие.  
  
## <a name="see-also"></a>См. также:  
   [интерфейса идебугаппликатионнодивентс](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
 [Идебугаппликатионнодивентс:: onattach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)   
 [Интерфейс IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)