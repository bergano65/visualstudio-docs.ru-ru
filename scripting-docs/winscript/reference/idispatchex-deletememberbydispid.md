---
title: IDispatchEx::DeleteMemberByDispID | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: de99e74cf12939a31c99cdc59ce8ad7fd685ae03
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086870"
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
 Идентификатор элемента. Использует `GetDispID` или `GetNextDispID` получить идентификатор диспетчеризации.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|||  
|-|-|  
|`S_OK`|Выполнено.|  
|`S_FALSE`|Элемент существует, но не может быть удален.|  
  
## <a name="remarks"></a>Примечания  
 Если элемент удаляется, идентификатор DISPID должен оставаться допустимым для `GetNextDispID`.  
  
 Если удаляется элемент с заданным именем и более поздней версии воссоздается член с тем же именем, идентификатор DISPID должны совпадать. (Имена элементов, которые отличаются только регистром, совпадают ли «» зависит от объекта.)  
  
## <a name="example"></a>Пример  
  
```cpp
BSTR bstrName;  
DISPID dispid;  
IDispatchEx *pdex;   
  
// Assign to pdex and bstrName  
if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
    pdex->DeleteMemberByDispID(dispid);  
```  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)