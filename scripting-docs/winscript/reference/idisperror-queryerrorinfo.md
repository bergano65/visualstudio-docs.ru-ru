---
title: "IDispError::QueryErrorInfo | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispError.QueryErrorInfo
apilocation: scrobj.dll
helpviewer_keywords: IDispError::QueryErrorInfo
ms.assetid: e7e71a14-77e2-4331-9ffc-1dace041fa84
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a165edf2d8f9a0b386daa0035ece1a722401a443
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idisperrorqueryerrorinfo"></a>IDispError::QueryErrorInfo
Возвращает определенный тип сведений об ошибках.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT QueryErrorInfo(  
   GUID  guidErrorType,  
   IDispError**  ppde  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `guidErrorType`  
 [in] Идентификатор GUID, указав тип ошибки.  
  
 `ppde`  
 [out] Указывает объект IDispError.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 `QueryErrorInfo` Метод извлекает сведения об ошибках определенного типа.  
  
> [!NOTE]
>  Этот метод не реализован.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDispError](../../winscript/reference/idisperror-interface.md)