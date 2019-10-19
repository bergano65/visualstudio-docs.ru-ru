---
title: 'Идисперрор:: Жеселпинфо | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetHelpInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetHelpInfo
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a84e57e97bb781ad3ea0be1ac6766fd94f6f5c30
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573135"
---
# <a name="idisperrorgethelpinfo"></a>IDispError::GetHelpInfo
Возвращает путь к файлу справки и идентификатор контекста раздела, в котором объясняется ошибка, если это возможно.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrFileName`  
 заполняет Строка, содержащая полный путь к файлу справки. Если файл справки отсутствует или возникает ошибка, возвращается значение NULL.  
  
 `pdwContext`  
 заполняет Идентификатор контекста справки для ошибки. Если файл справки отсутствует (если `pbstrFileName` имеет значение NULL), этот параметр не имеет смысла.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Произошла ошибка конкретного поставщика.|  
|`E_INVALIDARG`|`pbstrFileName` или `pdwContext` имел значение NULL.|  
|`E_OUTOFMEMORY`|Поставщику не удалось выделить достаточно памяти для получения пути к файлу справки.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод возвращает путь к файлу справки и идентификатор контекста раздела, поясняющего ошибку, если это возможно.  
  
> [!NOTE]
> Этот метод не реализован.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDispError](../../winscript/reference/idisperror-interface.md)