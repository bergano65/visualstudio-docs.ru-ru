---
title: IDebugExpression::GetResultAsDebugProperty | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsDebugProperty
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsDebugProperty
ms.assetid: 9075bf2f-d5bb-464e-b6c2-3fa3215e9ae0
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6ce67df5dd55bd8c1ae55bb19fe2a19aed9e40f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727114"
---
# <a name="idebugexpressiongetresultasdebugproperty"></a>IDebugExpression::GetResultAsDebugProperty
Возвращает результат вычисления выражения, как свойство отладки и возвращаемое значение операции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetResultAsDebugProperty(  
   HRESULT*          phrResult,  
   IDebugProperty**  ppdp  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `phrResult`  
 [out] Возвращаемое значение операции.  
  
 `ppdp`  
 [out] Свойство отладки для выражения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_PENDING`|Операция по-прежнему ожидание.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает результат вычисления выражения как `IDebugProperty` и операции `HRESULT`.  
  
 Этот метод возвращает `S_OK` и `phrResult` возвращает `E_ABORT` Если `Abort` прерывает операцию.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugExpression](../../winscript/reference/idebugexpression-interface.md)   
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)