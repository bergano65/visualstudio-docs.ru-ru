---
title: "IApplicationDebugger::QueryAlive | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IApplicationDebugger.QueryAlive
apilocation: scrobj.dll
helpviewer_keywords: IApplicationDebugger::QueryAlive
ms.assetid: 41181ebb-a3bf-4e41-82af-d6c7348dc706
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 48571476407c29b9af949bd6f626d14ea822f2e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggerqueryalive"></a>IApplicationDebugger::QueryAlive
Указывает, является ли отладчик отвечать на запросы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT QueryAlive();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметры.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод указывает, является ли отладчик отвечать на запросы. Реализации этого метода всегда должны возвращать `S_OK`.  
  
 Если непредвиденное завершение процесса отладчика COM возвращает ошибку из маршалинга прокси для вызова этого метода.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)