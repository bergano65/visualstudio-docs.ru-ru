---
title: IDispatchEx::D Елетемембербидиспид | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByDispID method
ms.assetid: f61231e5-ba93-4ac3-bde8-d363548356b3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c3dbb040e39fd15b77e42b2eaa9fb2cdda0b1b2
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144640"
---
# <a name="idispatchexdeletememberbydispid"></a>IDispatchEx::DeleteMemberByDispID
Удаляет элемент по DISPID.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT DeleteMemberByDispID(  
    DISPID id  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `id`  
 Идентификатор элемента. Использует `GetDispID` или `GetNextDispID` для получения идентификатора диспетчеризации.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Значение|Значение|
|-|-|  
|`S_OK`|Успех.|  
|`S_FALSE`|Элемент существует, но не может быть удален.|  
  
## <a name="remarks"></a>Remarks  
 Если элемент удален, идентификатор DISPID должен оставаться допустимым для `GetNextDispID` .  
  
 Если элемент с заданным именем удаляется, а позднее элемент с таким же именем создается повторно, идентификатор DISPID должен быть таким же. (Имена элементов, отличающиеся только регистром, являются "одинаковыми", зависит от объекта.)  
  
## <a name="example"></a>Пример  
  
```cpp
BSTR bstrName;  
DISPID dispid;  
IDispatchEx *pdex;   
  
// Assign to pdex and bstrName  
if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
    pdex->DeleteMemberByDispID(dispid);  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Интерфейс IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx:: Жетдиспид](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)