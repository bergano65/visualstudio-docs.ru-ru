---
title: "IDispError::GetHresult | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispError.GetHresult
apilocation: scrobj.dll
helpviewer_keywords: IDispError::GetHresult
ms.assetid: a14d566e-473f-497b-a2f9-85331433e6c9
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 859708b8aec4f89dd1ea49bf6e248d7bcade7624
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idisperrorgethresult"></a>IDispError::GetHresult
Получает код ошибки из `IDispError` объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetHresult(  
   HRESULT*  phr  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `phr`  
 [out] Указывает код ошибки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод получает код ошибки из `IDispError` объекта.  
  
> [!NOTE]
>  Этот метод не реализован.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDispError](../../winscript/reference/idisperror-interface.md)