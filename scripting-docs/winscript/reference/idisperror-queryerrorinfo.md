---
title: 'Идисперрор:: Куерерроринфо | Документация Майкрософт'
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
ms.openlocfilehash: 5ccfcb020faf25fbe1723a384ff08aefcf55b56d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573076"
---
# <a name="idisperrorqueryerrorinfo"></a>IDispError::QueryErrorInfo
Извлекает сведения об ошибке определенного типа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT QueryErrorInfo(  
   GUID  guidErrorType,  
   IDispError**  ppde  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `guidErrorType`  
 окне Идентификатор GUID, указывающий тип ошибки.  
  
 `ppde`  
 заполняет Указывает объект Идисперрор.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Метод `QueryErrorInfo` извлекает сведения об ошибке определенного типа.  
  
> [!NOTE]
> Этот метод не реализован.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDispError](../../winscript/reference/idisperror-interface.md)