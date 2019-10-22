---
title: 'Идебугасинкоператион:: Abort | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Abort
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Abort
ms.assetid: 232541c6-81b8-4eb7-96a7-a8e5fe087b31
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9ca6c5e1498229c84dc28a13cda2cce77b58a4f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573296"
---
# <a name="idebugasyncoperationabort"></a>IDebugAsyncOperation::Abort
Отменяет операцию.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Abort();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|S_OK|Метод успешно выполнен.|  
|E_NOTIMPL|Операции не могут быть отменены.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод обычно вызывается из потока отладчика для отмены неотвечающей операции. Этот метод вызывает вызов метода `InProgressAbort` для объекта `IDebugSyncOperation`.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса идебугасинкоператион](../../winscript/reference/idebugasyncoperation-interface.md)  
 [Идебугасинкоператион:: Start](../../winscript/reference/idebugasyncoperation-start.md)    
 [IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)