---
title: 'Иенумдебугпропертинфо:: Next | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Next
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Next
ms.assetid: 052837ac-1599-49cc-9a5a-ba90f992eeff
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b99631c217ca56dce91512403dfb6623cd1e7641
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574196"
---
# <a name="ienumdebugpropertyinfonext"></a>IEnumDebugPropertyInfo::Next
Извлекает указанное число структур `DebugPropertyInfo` в последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Next (  
   ULONGcelt,  
   DebugPropertyInfo*rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 окне Число извлекаемых `DebugPropertyInfo`structures.  
  
 `rgelt`  
 заполняет Массив извлеченных структур `DebugPropertyInfo`.  
  
 `pceltFetched`  
 заполняет Возвращает число фактически извлеченных структур `DebugPropertyInfo`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает допустимый `HRESULT`, обычно `S_OK`.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса иенумдебугпропертинфо](../../winscript/reference/ienumdebugpropertyinfo-interface.md)  
 [Структура DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)