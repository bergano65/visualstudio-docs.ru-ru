---
title: IRemoteDebugApplication::DisconnectDebugger | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.DisconnectDebugger
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::DisconnectDebugger
ms.assetid: 989e5a34-0267-4a2e-96b6-e1dcc2ffe883
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9ff016752116664ca2c2cf71a7676fcb6a14ab61
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151080"
---
# <a name="iremotedebugapplicationdisconnectdebugger"></a>IRemoteDebugApplication::DisconnectDebugger
Отключает текущий отладчик от приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT DisconnectDebugger();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод отключает текущий отладчик от приложения.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)