---
title: "IDebugApplication::GetCurrentThread | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.GetCurrentThread
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::GetCurrentThread
ms.assetid: 15128e77-6fc6-42a2-8c04-20e22ef03f29
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2240a62b62c917e94f3ace8f516a10f9de66c74d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationgetcurrentthread"></a>IDebugApplication::GetCurrentThread
Возвращает поток, связанный с текущим выполняемым потоком.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetCurrentThread(  
   IDebugApplicationThread**  pat  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pat`  
 [out] Поток, связанный с текущим выполняемым потоком.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает поток, связанный с текущим выполняемым потоком.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)