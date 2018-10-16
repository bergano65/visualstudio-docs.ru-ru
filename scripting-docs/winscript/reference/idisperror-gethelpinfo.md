---
title: IDispError::GetHelpInfo | Документы Microsoft
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
ms.openlocfilehash: 17098b4055bb61e9a2f639404edfe2214abc931e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728014"
---
# <a name="idisperrorgethelpinfo"></a>IDispError::GetHelpInfo
Возвращает путь к файлу справки и идентификатор контекста раздела справки, который описывает ее, если это возможно.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrFileName`  
 [out] Строка, содержащая полный путь файла справки. Если файл справки отсутствует или возникает ошибка, возвращается значение NULL.  
  
 `pdwContext`  
 [out] Идентификатор контекста справки для ошибки. Если отсутствует файл справки (если `pbstrFileName` имеет значение NULL), этот параметр не имеет смысла.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Ошибка поставщика.|  
|`E_INVALIDARG`|`pbstrFileName`или `pdwContext` был равен NULL.|  
|`E_OUTOFMEMORY`|Поставщик не удалось выделить достаточный объем памяти, в которую возвращается путь к файлу справки.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает путь к файлу справки и идентификатор контекста раздела справки, который описывает ее, если это возможно.  
  
> [!NOTE]
>  Этот метод не реализован.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDispError](../../winscript/reference/idisperror-interface.md)