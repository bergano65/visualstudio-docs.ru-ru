---
title: 'Идисперрор:: ondescription | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetDescription
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetDescription
ms.assetid: 04deaea6-0265-4e34-952e-634edba0e923
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d1bb1c3516c2601707e1a0bcd69f4f8409514fe
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573139"
---
# <a name="idisperrorgetdescription"></a>IDispError::GetDescription
Возвращает текстовое описание ошибки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetDescription(  
   BSTR*  pbstrDescription  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrDescription`  
 заполняет Строка, содержащая краткое описание ошибки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Текст возвращается на языке, указанном кодом локали (LCID), который был передан `IDispatchEx::InvokeEx` для метода, который вызвал ошибку.  
  
> [!NOTE]
> Этот метод не реализован.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса идисперрор](../../winscript/reference/idisperror-interface.md)  
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)