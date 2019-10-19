---
title: 'Идебужекспрессионкаллбакк:: OnComplete | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpressionCallBack.onComplete
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugExpressionCallBack::onComplete
ms.assetid: d0b89db3-38e7-44e0-93fe-60205f9149dd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1fd142cc7ecbcd984be1943da05fa782260b10f8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576423"
---
# <a name="idebugexpressioncallbackoncomplete"></a>IDebugExpressionCallBack::onComplete
Указывает, что вычисление выражения завершено.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT onComplete();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод вызывается после завершения вычисления выражения. В этом обработчике событий можно вызвать метод `IDebugExpression::GetResultAsString`.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса идебужекспрессионкаллбакк](../../winscript/reference/idebugexpressioncallback-interface.md)  
 [IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)