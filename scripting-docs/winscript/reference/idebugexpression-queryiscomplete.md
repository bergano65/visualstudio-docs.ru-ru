---
title: IDebugExpression::QueryIsComplete | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.QueryIsComplete
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::QueryIsComplete
ms.assetid: 510d62e5-a316-46fb-b23f-d3ba902b295c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0b4fa4b027f0ee8d848f52c063cbfd1f7679d4a6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087156"
---
# <a name="idebugexpressionqueryiscomplete"></a>IDebugExpression::QueryIsComplete
Определяет, если операция будет завершена.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT QueryIsComplete();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод выполнен успешно, и операция будет завершена.|  
|`S_FALSE`|Операция по-прежнему не ожидается.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод определяет, если операция будет завершена.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugExpression](../../winscript/reference/idebugexpression-interface.md)