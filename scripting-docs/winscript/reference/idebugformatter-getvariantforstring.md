---
title: IDebugFormatter::GetVariantForString | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugFormatter.GetVariantForString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugFormatter::GetVariantForString
ms.assetid: 2993431d-0ee2-4d8d-b62c-0a810a8bc391
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea6cd1f77481282700de492e2857046044a04e2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979293"
---
# <a name="idebugformattergetvariantforstring"></a>IDebugFormatter::GetVariantForString
Возвращает значение VARIANT, содержащая заданную строку.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetVariantForString(  
   LPCOLESTR  pwstrValue,  
   VARIANT*   pvar  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pwstrValue`  
 [in] Строка для хранения в ВАРИАНТЕ.  
  
 `pvar`  
 [out] Типа VARIANT, содержащее `pwstrValue`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает значение VARIANT, содержащая заданную строку.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugFormatter](../../winscript/reference/idebugformatter-interface.md)