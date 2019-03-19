---
title: IEnumDebugExtendedPropertyInfo::Next | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.Next
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::Next
ms.assetid: ac41c9a3-19d1-4596-8a87-01c10b131be3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 65e734d1cf57fe9387407a80c9d3e76d7f53ada8
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151925"
---
# <a name="ienumdebugextendedpropertyinfonext"></a>IEnumDebugExtendedPropertyInfo::Next
Извлекает указанное число`ExtendedDebugPropertyInfo` структур в последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Next (  
   ULONGcelt,  
   ExtendedDebugPropertyInfo *rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 [in] Количество `ExtendedDebugPropertyInfo`структур, которые требуется извлечь.  
  
 `rgelt`  
 [out] Массив `ExtendedDebugPropertyInfo` получить структур.  
  
 `pceltFetched`  
 [out] Количество `ExtendedDebugPropertyInfo` фактически извлеченных структур.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает допустимый `HRESULT`, обычно `S_OK`.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IEnumDebugExtendedPropertyInfo](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [Структура ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)