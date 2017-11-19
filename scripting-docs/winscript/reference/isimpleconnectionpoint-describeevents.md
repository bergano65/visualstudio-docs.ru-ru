---
title: "ISimpleConnectionPoint::DescribeEvents | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ISimpleConnectionPoint.DescribeEvents
apilocation: pdm.dll
helpviewer_keywords: ISimpleConnectionPoint::DescribeEvents
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 42dab9558d46eae0fbb640c60264a79877708321
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
Возвращает идентификатор DISPID и имя для каждого события в указанном диапазоне событий.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 [in] Индекс первого события для получения.  
  
 `cEvents`  
 [in] Количество событий для получения.  
  
 `prgid`  
 [out] Массив значений DISPID событий.  
  
 `prgbstr`  
 [out] Массив имен событий.  
  
 `pcEventsFetched`  
 [out] Фактическое число выбранных событий.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`S_FALSE`|Дополнительные события были запрошены не были доступны. Недоступен события представлены с DISPID_NULL и null BSTR.|  
|`E_INVALIDARG`|Не удалось получить.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает DISPID и имя для каждого события в указанном диапазоне событий.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)