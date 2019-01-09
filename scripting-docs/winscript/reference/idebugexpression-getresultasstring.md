---
title: IDebugExpression::GetResultAsString | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 6cee33b5547e30f913407b02a3befd449dda6aeb
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097361"
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
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_PENDING`|Операция по-прежнему не ожидается.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает результат вычисления выражения в виде строки, а также операции `HRESULT`.  
  
 Этот метод возвращает `S_OK` и `phrResult` возвращает `E_ABORT` Если `Abort` прерывает выполнение операции.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugExpression](../../winscript/reference/idebugexpression-interface.md)