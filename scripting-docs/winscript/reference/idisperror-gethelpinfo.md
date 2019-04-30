---
title: IDispError::GetHelpInfo | Документация Майкрософт
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
ms.openlocfilehash: fa831ff511ea507e03ca858b93383ff38ead9039
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446910"
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
> Этот метод не реализован.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDispError](../../winscript/reference/idisperror-interface.md)