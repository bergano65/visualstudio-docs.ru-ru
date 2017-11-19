---
title: "IDebugAsyncOperation::QueryIsComplete | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugAsyncOperation.QueryIsComplete
apilocation: pdm.dll
helpviewer_keywords: IDebugAsyncOperation::QueryIsComplete
ms.assetid: fcf6e229-4d40-46d9-ab81-d3561bc8e084
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e985697e425ec4966f2260792a9698fa50b4c98d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugasyncoperationqueryiscomplete"></a>IDebugAsyncOperation::QueryIsComplete
Определяет, если завершения отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT QueryIsComplete();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметры.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Операция будет завершена.|  
|`S_FALSE`|Операция не завершена.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод определяет, если завершения отладки.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)