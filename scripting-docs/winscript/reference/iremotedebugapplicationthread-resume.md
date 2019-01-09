---
title: IRemoteDebugApplicationThread::Resume | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.Resume
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::Resume
ms.assetid: ac290861-515d-4f06-b452-3b96f54e538c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cd48bc881c9f5ab08fc6e75b2ef7f0b1cf470bbe
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086883"
---
# <a name="iremotedebugapplicationthreadresume"></a>IRemoteDebugApplicationThread::Resume
Возобновляет выполнение потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Resume(  
   DWORD*  pdwCount  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdwCount`  
 [out] Счетчик приостановки для потока.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Когда этот метод возобновляет работу потока, он уменьшает счетчик приостановок.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)