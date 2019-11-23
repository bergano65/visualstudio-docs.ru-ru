---
title: 'Идебужекспрессион:: Start | Документация Майкрософт'
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
ms.openlocfilehash: 1c8c3666adfc83f3ad60b942cd3f7fe9eedfccba
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576429"
---
# <a name="idebugexpressionstart"></a>IDebugExpression::Start
Начинает вычисление выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Start(  
   IDebugExpressionCallBack*  pdecb  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdecb`  
 окне Обратный вызов для указания завершения вычисления выражения. Если этот параметр имеет значение `NULL`, события не срабатывают и клиент должен опросить состояние выражения с помощью `QueryIsComplete`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод начинает вычисление выражения.  
  
## <a name="see-also"></a>См. также:  
 [Идебужекспрессион:: Abort](../../winscript/reference/idebugexpression-abort.md)   
 [Интерфейс IDebugExpression](../../winscript/reference/idebugexpression-interface.md)