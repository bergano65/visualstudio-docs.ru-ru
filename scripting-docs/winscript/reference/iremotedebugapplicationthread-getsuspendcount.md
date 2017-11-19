---
title: "IRemoteDebugApplicationThread::GetSuspendCount | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplicationThread.GetSuspendCount
apilocation: pdm.dll
helpviewer_keywords: IRemoteDebugApplicationThread::GetSuspendCount
ms.assetid: 37f9936c-fd7c-412d-9a7f-628ca3a90438
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1ddfde0b9348db25c9949be24007c55afdd3b54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationthreadgetsuspendcount"></a>IRemoteDebugApplicationThread::GetSuspendCount
Возвращает счетчик приостановки для потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetSuspendCount(  
   DWORD*  pdwCount  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdwCount`  
 [out] Счетчик приостановки для потока.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает счетчик приостановки для потока.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)