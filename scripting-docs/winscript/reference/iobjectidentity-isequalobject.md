---
title: "IObjectIdentity::IsEqualObject | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IObjectIdentity.IsEqualObject
apilocation:
- scrobj.dll
helpviewer_keywords:
- IsEqualObject method
ms.assetid: 78c5c5c2-d299-4036-986c-7c1d87cbe7cd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 52e386055e458568f8d4076a37489b7b2397f399
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iobjectidentityisequalobject"></a>IObjectIdentity::IsEqualObject
Определяет, является ли объект равен текущему объекту.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT IsEqualObject(  
  IUnknown*punk  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `punk`  
 [in] Адрес объекта, сравниваемый с текущим объектом.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Объекты равны.|  
|`S_FALSE`|Объекты не равны.|  
  
## <a name="remarks"></a>Примечания  
 Реализация `IsEqualObject` метод должен возвращать `S_OK` только в том случае, если объекты совпадают.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IObjectIdentity](../../winscript/reference/iobjectidentity-interface.md)