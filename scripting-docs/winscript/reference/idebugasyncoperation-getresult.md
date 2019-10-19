---
title: Идебугасинкоператион::/результат | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.GetResult
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::GetResult
ms.assetid: 56d43365-6b12-4213-a97c-953c40d7b7f6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55c51649a5bc3094dd306166e013a892ce67e236
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573288"
---
# <a name="idebugasyncoperationgetresult"></a>IDebugAsyncOperation::GetResult
Предоставляет возвращаемое значение и параметр возвращаемого объекта из синхронной операции отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `phrResult`  
 заполняет Если операция завершена, `phrResult` является возвращаемым значением `IDebugSyncOperation::Execute`.  
  
 `ppunkResult`  
 заполняет Если операция завершена, `ppunkResult` является параметром объекта, возвращаемым операцией.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_PENDING`|Операция не завершена.|  
  
## <a name="remarks"></a>Заметки  
 Если операция завершена, этот метод возвращает `HRESULT` и параметр объекта из `IDebugSyncOperation::Execute`.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса идебугасинкоператион](../../winscript/reference/idebugasyncoperation-interface.md)  
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)