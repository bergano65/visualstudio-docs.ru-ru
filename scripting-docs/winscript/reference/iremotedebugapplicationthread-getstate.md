---
title: Иремотедебугаппликатионсреад::/State | Документация Майкрософт
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
ms.openlocfilehash: 42f7f2a292c908b5fe49f1097b0fe56b8b0b11e0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575249"
---
# <a name="iremotedebugapplicationthreadgetstate"></a>IRemoteDebugApplicationThread::GetState
Возвращает состояние этого потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetState(  
   DWORD*  pState  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pState`  
 заполняет Сочетание следующих флагов состояния потока:  
  
|Константа|значения|Описание|  
|--------------|-----------|-----------------|  
|THREAD_STATE_RUNNING|0x00000001|Поток работает.|  
|THREAD_STATE_SUSPENDED|0x00000002|Поток приостановлен.|  
|THREAD_BLOCKED|0x00000004|Поток заблокирован.|  
|THREAD_OUT_OF_CONTEXT|0x00000008|Поток находится за пределами содержимого.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод получает состояние этого потока.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)