---
title: IDebugFormatter::GetVariantForString | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 1ee40057043751b465c6575575f00dee848a0160
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086623"
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
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает значение VARIANT, содержащая заданную строку.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugFormatter](../../winscript/reference/idebugformatter-interface.md)