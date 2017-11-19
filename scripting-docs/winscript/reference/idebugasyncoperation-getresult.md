---
title: "IDebugAsyncOperation::GetResult | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugAsyncOperation.GetResult
apilocation: pdm.dll
helpviewer_keywords: IDebugAsyncOperation::GetResult
ms.assetid: 56d43365-6b12-4213-a97c-953c40d7b7f6
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60181904408010f35fa4d99d182216e665583aab
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugasyncoperationgetresult"></a>IDebugAsyncOperation::GetResult
Предоставляет параметр возвращаемого объекта из отладки синхронной операции и возвращаемое значение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `phrResult`  
 [out] Если операция будет завершена, `phrResult` имеет возвращаемое значение `IDebugSyncOperation::Execute`.  
  
 `ppunkResult`  
 [out] Если операция будет завершена, `ppunkResult` параметром объекта, возвращенное операцией.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_PENDING`|Операция не завершена.|  
  
## <a name="remarks"></a>Примечания  
 Если операция завершена, этот метод возвращает `HRESULT` и параметра из объекта `IDebugSyncOperation::Execute`.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)