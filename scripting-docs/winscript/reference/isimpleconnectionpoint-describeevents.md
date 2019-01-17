---
title: ISimpleConnectionPoint::DescribeEvents | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.DescribeEvents
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::DescribeEvents
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 43a20a2d9580c80bc6aea5d22c6a0713f4843634
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088508"
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
Возвращает идентификатор DISPID и имя для каждого события в указанном диапазоне событий.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT DescribeEvents(  
   ULONG    iEvent,  
   ULONG    cEvents,  
   DISPID*  prgid,  
   BSTR*    prgbstr,  
   ULONG*   pcEventsFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `iEvent`  
 [in] Индекс первого события для извлечения.  
  
 `cEvents`  
 [in] Количество событий для получения.  
  
 `prgid`  
 [out] Массив значений DISPID событий.  
  
 `prgbstr`  
 [out] Массив имен событий.  
  
 `pcEventsFetched`  
 [out] Фактическое число извлечь события.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`S_FALSE`|Были запрошены дополнительные события, не были доступны. Недоступны события представляются с DISPID_NULL и null BSTR.|  
|`E_INVALIDARG`|Элементы не удалось получить.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает идентификатор DISPID и имя для каждого события в указанном диапазоне событий.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)