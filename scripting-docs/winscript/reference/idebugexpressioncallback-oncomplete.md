---
title: IDebugExpressionCallBack::onComplete | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: fa3d7d6173161407619174607eae221e4513cbcd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727554"
---
# <a name="idebugexpressioncallbackoncomplete"></a>IDebugExpressionCallBack::onComplete
Указывает полный вычисления выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT onComplete();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметры.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается после завершения вычисления выражения. `IDebugExpression::GetResultAsString` Метод может вызываться из этого обработчика событий.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugExpressionCallBack](../../winscript/reference/idebugexpressioncallback-interface.md)   
 [IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)