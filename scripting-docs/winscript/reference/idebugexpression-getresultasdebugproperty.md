---
title: 'Идебужекспрессион:: Жетресултасдебугпроперти | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 104c42f02d02be386711e687f02d333425834948
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575930"
---
# <a name="idebugexpressiongetresultasdebugproperty"></a>IDebugExpression::GetResultAsDebugProperty
Возвращает результат вычисления выражения как свойство Debug и возвращаемое значение операции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetResultAsDebugProperty(  
   HRESULT*          phrResult,  
   IDebugProperty**  ppdp  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `phrResult`  
 заполняет Возвращаемое значение операции.  
  
 `ppdp`  
 заполняет Свойство Debug для выражения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_PENDING`|Операция все еще находится в состоянии ожидания.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод возвращает результат вычисления выражения в виде `IDebugProperty` и `HRESULT` операции.  
  
 Этот метод возвращает `S_OK` и `phrResult` возвращает `E_ABORT`, если `Abort` прерывает операцию.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса идебужекспрессион](../../winscript/reference/idebugexpression-interface.md)  
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)