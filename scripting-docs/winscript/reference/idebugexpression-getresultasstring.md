---
title: "IDebugExpression::GetResultAsString | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugExpression.GetResultAsString
apilocation: jscript.dll
helpviewer_keywords: IDebugExpression::GetResultAsString
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 557fe65859d1e3046d64884982070ad233e12559
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressiongetresultasstring"></a>IDebugExpression::GetResultAsString
Возвращает результат вычисления выражения, как строка и возвращаемое значение операции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `phrResult`  
 [out] Возвращаемое значение операции.  
  
 `pbstrResult`  
 [out] Результат вычисления выражения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_PENDING`|Операция по-прежнему ожидание.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает результат вычисления выражения, как строка и операции `HRESULT`.  
  
 Этот метод возвращает `S_OK` и `phrResult` возвращает `E_ABORT` Если `Abort` прерывает операцию.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugExpression](../../winscript/reference/idebugexpression-interface.md)