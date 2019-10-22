---
title: 'Идебужекспрессион:: Жетресултасстринг | Документация Майкрософт'
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
ms.openlocfilehash: 56b8f637744227763f55b7c024745d7ae4448b40
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573517"
---
# <a name="idebugexpressiongetresultasstring"></a>IDebugExpression::GetResultAsString
Возвращает результат вычисления выражения в виде строки и возвращаемого значения операции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `phrResult`  
 заполняет Возвращаемое значение операции.  
  
 `pbstrResult`  
 заполняет Результат вычисления выражения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_PENDING`|Операция все еще находится в состоянии ожидания.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод возвращает результат вычисления выражения в виде строки и `HRESULT` операции.  
  
 Этот метод возвращает `S_OK` и `phrResult` возвращает `E_ABORT`, если `Abort` прерывает операцию.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugExpression](../../winscript/reference/idebugexpression-interface.md)