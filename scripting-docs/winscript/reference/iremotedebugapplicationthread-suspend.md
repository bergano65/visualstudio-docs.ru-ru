---
title: "IRemoteDebugApplicationThread::Suspend | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplicationThread.Suspend
apilocation: pdm.dll
helpviewer_keywords: IRemoteDebugApplicationThread::Suspend
ms.assetid: fd5cc874-2970-4092-b1cd-e638775b0e20
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 995fa9e16fa9e1d712caff578c29b9aa3e14123b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationthreadsuspend"></a>IRemoteDebugApplicationThread::Suspend
Приостанавливает работу потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT Suspend(  
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
 Этот метод приостанавливает работу потока, увеличивается счетчик приостановок.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)