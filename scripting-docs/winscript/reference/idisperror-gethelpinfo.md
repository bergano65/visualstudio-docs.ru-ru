---
title: IDispError::GetHelpInfo | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 8c2c8ae3a3cff2485c50901bb94ced83098e6000
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087494"
---
# <a name="idisperrorgethelpinfo"></a>IDispError::GetHelpInfo
Возвращает путь к файлу справки и идентификатор раздела справки, который описывает ее, если это возможно.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrFileName`  
 [out] Строка, содержащая полный путь к файлу справки. Если нет файла справки или возникает ошибка, возвращается значение NULL.  
  
 `pdwContext`  
 [out] Идентификатор контекста справки для ошибки. Если нет файла справки (если `pbstrFileName` имеет значение NULL), этот параметр не имеет смысла.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Произошла ошибка поставщика.|  
|`E_INVALIDARG`|`pbstrFileName` или `pdwContext` был равен NULL.|  
|`E_OUTOFMEMORY`|Поставщик не удалось выделить достаточный объем памяти, в которую будет возвращен путь к файлу справки.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает путь к файлу справки, а также идентификатор контекста в разделе, который описывает ее, если это возможно.  
  
> [!NOTE]
>  Этот метод не реализован.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDispError](../../winscript/reference/idisperror-interface.md)