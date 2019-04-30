---
title: IDebugAsyncOperation::Start | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Start
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Start
ms.assetid: a7272364-28e0-48ae-8405-b8bce8a6b9fd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3e02869abab65878412f96b77d5782b9717a1b6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821932"
---
# <a name="idebugasyncoperationstart"></a>IDebugAsyncOperation::Start
Вызывает асинхронную операцию, чтобы начать.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Start(  
   IDebugAsyncOperationCallBack*  padocb  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `padocb`  
 Интерфейс обратного вызова, который получает состояние события из этой операции.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_UNEXPECTED`|Уже ожидается операция.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывает `IDebugSyncOperation::Execute` вызываемого асинхронно в потоке, полученный из `IDebugSyncOperation::GetTargetThread`. Этот метод должен вызываться только из потока отладчика; в противном случае он не вернет до завершения операции.  
  
## <a name="see-also"></a>См. также  
 [IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)   
 [Интерфейс IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)   
 [IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)