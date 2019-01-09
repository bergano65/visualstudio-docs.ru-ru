---
title: IDispError::GetHresult | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetHresult
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetHresult
ms.assetid: a14d566e-473f-497b-a2f9-85331433e6c9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 08020ea38c687cb0f69b1108935fd79802cc3120
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086285"
---
# <a name="idisperrorgethresult"></a>IDispError::GetHresult
Получает код ошибки из `IDispError` объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
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
 Этот метод возвращает код ошибки из `IDispError` объекта.  
  
> [!NOTE]
>  Этот метод не реализован.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDispError](../../winscript/reference/idisperror-interface.md)