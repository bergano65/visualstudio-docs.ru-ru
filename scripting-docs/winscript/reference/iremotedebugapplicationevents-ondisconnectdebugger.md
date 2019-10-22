---
title: 'IRemoteDebugApplicationEvents:: Ондисконнектдебугжер | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnDisconnectDebugger
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnDisconnectDebugger
ms.assetid: ea11cde0-1484-4181-a5dd-a1f6cf788892
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53e26da46fcdca0db0c8a652a091e95cd83789cd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575588"
---
# <a name="iremotedebugapplicationeventsondisconnectdebugger"></a>IRemoteDebugApplicationEvents::OnDisconnectDebugger
Обрабатывает событие отключения отладчика.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT OnDisconnectDebugger();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод обрабатывает событие отключения отладчика.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md)