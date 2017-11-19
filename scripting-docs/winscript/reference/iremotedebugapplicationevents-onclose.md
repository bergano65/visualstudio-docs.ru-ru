---
title: "IRemoteDebugApplicationEvents::OnClose | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplicationEvents.OnClose
apilocation: jscript.dll
helpviewer_keywords: IRemoteDebugApplicationEvents::OnClose
ms.assetid: 57ef69e0-1ced-480a-a1bf-c91d8d5dd2d2
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1bd38c08e1e15cbf0e5e9fdfd60c5ead128dbad
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationeventsonclose"></a>IRemoteDebugApplicationEvents::OnClose
Обрабатывает событие закрытия приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT OnClose();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметры.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод обрабатывает событие закрытия приложения.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md)