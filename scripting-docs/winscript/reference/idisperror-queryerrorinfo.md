---
title: IDispError::QueryErrorInfo | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.QueryErrorInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::QueryErrorInfo
ms.assetid: e7e71a14-77e2-4331-9ffc-1dace041fa84
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 32d887cad92de28df7e84f71fe6b991ada9067e2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160356"
---
# <a name="idisperrorqueryerrorinfo"></a>IDispError::QueryErrorInfo
Извлекает определенный тип сведений об ошибке.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
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
 `QueryErrorInfo` Метод извлекает определенный тип сведений об ошибке.  
  
> [!NOTE]
>  Этот метод не реализован.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDispError](../../winscript/reference/idisperror-interface.md)