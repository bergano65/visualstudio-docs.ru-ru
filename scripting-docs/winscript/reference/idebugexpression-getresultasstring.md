---
title: IDebugExpression::GetResultAsString | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsString
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 84255e364630245564a0cbab5d38c6dff38df0a8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978476"
---
# <a name="idebugexpressiongetresultasstring"></a>IDebugExpression::GetResultAsString
Возвращает результат вычисления выражения в виде строки, а возвращаемое значение операции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
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
|`E_PENDING`|Операция по-прежнему не ожидается.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает результат вычисления выражения в виде строки, а также операции `HRESULT`.  
  
 Этот метод возвращает `S_OK` и `phrResult` возвращает `E_ABORT` Если `Abort` прерывает выполнение операции.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugExpression](../../winscript/reference/idebugexpression-interface.md)