---
title: "IDebugApplicationThread::QueryIsDebuggerThread | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplicationThread.QueryIsDebuggerThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::QueryIsDebuggerThread
ms.assetid: 78a9cfbf-7c62-4aab-82a2-35037e2f9d46
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c3ad00fafa602b7a2f55b0412ae16c82cc2f5bf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthreadqueryisdebuggerthread"></a>IDebugApplicationThread::QueryIsDebuggerThread
Определяет, является ли этот поток потока отладчика.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT QueryIsDebuggerThread();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметры.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен, и это поток отладки.|  
|`S_FALSE`|Это не поток отладки.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод определяет, является ли этот поток потока отладчика.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)