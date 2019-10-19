---
title: 'IDebugFormatter:: Жетвариантфорстринг | Документация Майкрософт'
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
ms.openlocfilehash: fc230caa861444b10b463e5786d5f8cb93ec32f7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571514"
---
# <a name="idebugformattergetvariantforstring"></a>IDebugFormatter::GetVariantForString
Возвращает значение типа VARIANT, содержащее заданную строку.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetVariantForString(  
   LPCOLESTR  pwstrValue,  
   VARIANT*   pvar  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pwstrValue`  
 окне Строка для хранения в ВАРИАНТе.  
  
 `pvar`  
 заполняет ВАРИАНТ, содержащий `pwstrValue`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод возвращает значение типа VARIANT, содержащее заданную строку.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugFormatter](../../winscript/reference/idebugformatter-interface.md)