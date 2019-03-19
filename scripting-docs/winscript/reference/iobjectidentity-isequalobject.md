---
title: IObjectIdentity::IsEqualObject | Документация Майкрософт
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
ms.openlocfilehash: c215a15a1239f07272079783366a1617c3a626e2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58156038"
---
# <a name="iobjectidentityisequalobject"></a>IObjectIdentity::IsEqualObject
Определяет, если объект равен текущему объекту.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT IsEqualObject(  
  IUnknown*punk  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `punk`  
 [in] Адрес объекта, сравниваемый с текущим объектом.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Объекты равны.|  
|`S_FALSE`|Объекты не равны.|  
  
## <a name="remarks"></a>Примечания  
 Реализация `IsEqualObject` метод должен возвращать `S_OK` только в том случае, если объекты идентичны.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IObjectIdentity](../../winscript/reference/iobjectidentity-interface.md)