---
title: IActiveScriptError::GetExceptionInfo | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetExceptionInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetExceptionInfo
ms.assetid: 528416cc-8468-4ad7-a6c2-fa1daf6ecf33
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 71e8f787e6837e6fa41c7b3cd831448b5d20a95e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009575"
---
# <a name="iactivescripterrorgetexceptioninfo"></a>IActiveScriptError::GetExceptionInfo
Извлекает сведения об ошибке, которая произошла во время выполнения сценария обработчик сценариев.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetExceptionInfo(  
    EXCEPINFO *pexcepinfo  // structure for exception information  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pexcepinfo`  
 [out] Адрес `EXCEPINFO` структуру, которая получает сведения об ошибке.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` в случае успешного выполнения или `E_FAIL` Если произошла ошибка.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)