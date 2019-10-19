---
title: 'Иобжектидентити:: Исекуалобжект | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IObjectIdentity.IsEqualObject
apilocation:
- scrobj.dll
helpviewer_keywords:
- IsEqualObject method
ms.assetid: 78c5c5c2-d299-4036-986c-7c1d87cbe7cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 636dfa07b1fc94dfec2273220aa4101f5cd085b1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571472"
---
# <a name="iobjectidentityisequalobject"></a>IObjectIdentity::IsEqualObject
Определяет, равен ли объект текущему объекту.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT IsEqualObject(  
  IUnknown*punk  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `punk`  
 окне Адрес объекта для сравнения с текущим объектом.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Объекты равны.|  
|`S_FALSE`|Объекты не равны.|  
  
## <a name="remarks"></a>Заметки  
 Реализация метода `IsEqualObject` должна возвращать `S_OK` только в том случае, если объекты идентичны.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IObjectIdentity](../../winscript/reference/iobjectidentity-interface.md)