---
title: Исимплеконнектионпоинт::D Ескрибивентс | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: b5000689d588fe3f63ec5408893187bba8d13d63
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571824"
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
 окне Индекс первого извлекаемого события.  
  
 `cEvents`  
 окне Число извлекаемых событий.  
  
 `prgid`  
 заполняет Массив значений DISPID события.  
  
 `prgbstr`  
 заполняет Массив имен событий.  
  
 `pcEventsFetched`  
 заполняет Фактическое число выбранных событий.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`S_FALSE`|Запрошено больше событий, чем было доступно. Недоступные события представлены с помощью DISPID_NULL и NULL BSTR.|  
|`E_INVALIDARG`|Не удалось извлечь элементы.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод возвращает идентификатор DISPID и имя для каждого события в указанном диапазоне событий.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)