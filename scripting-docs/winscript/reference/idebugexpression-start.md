---
title: IDebugExpression::Start | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.Start
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::Start
ms.assetid: a7af3470-62b5-40f0-987d-63b6b22538b3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e80f3fb8087d39c76f59cf5c6bc8719c1cbaf5e4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978527"
---
# <a name="idebugexpressionstart"></a>IDebugExpression::Start
Начинается вычисление выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Start(  
   IDebugExpressionCallBack*  pdecb  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdecb`  
 [in] Обратный вызов, указывающий при завершении вычисления выражения. Если этот параметр имеет `NULL`, не возникает никаких событий, и клиент должен опросить состояние выражения с помощью `QueryIsComplete`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод начинает вычисления выражения.  
  
## <a name="see-also"></a>См. также  
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)   
 [Интерфейс IDebugExpression](../../winscript/reference/idebugexpression-interface.md)