---
title: IRemoteDebugApplicationThread::GetState | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.GetState
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::GetState
ms.assetid: 44503a78-efa9-4fbf-98be-a5dcfa329c5a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6534f57c92776dcd3cde9083335becbd66002a32
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788121"
---
# <a name="iremotedebugapplicationthreadgetstate"></a>IRemoteDebugApplicationThread::GetState
Получает состояние данного потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetState(  
   DWORD*  pState  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pState`  
 [out] Сочетание следующих флагов состояния потока:  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|THREAD_STATE_RUNNING|0x00000001|Поток выполняется.|  
|THREAD_STATE_SUSPENDED|0x00000002|Поток приостановлен.|  
|THREAD_BLOCKED|0x00000004|Поток блокируется.|  
|THREAD_OUT_OF_CONTEXT|0x00000008|Поток выходит за пределы содержимого.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает состояние данного потока.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)