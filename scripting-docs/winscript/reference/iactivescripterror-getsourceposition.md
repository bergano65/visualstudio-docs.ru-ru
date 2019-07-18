---
title: IActiveScriptError::GetSourcePosition | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetSourcePosition
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetSourcePosition
ms.assetid: ae9b26b1-82a7-4645-9686-3261d8248664
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4446235a9584bc45fad84b6f92ecc02592e554f3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009628"
---
# <a name="iactivescripterrorgetsourceposition"></a>IActiveScriptError::GetSourcePosition
Извлекает расположение в исходном коде, где произошла ошибка во время выполнения сценария обработчик сценариев.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetSourcePosition(  
    DWORD *pdwSourceContext,  // context cookie  
    ULONG *pulLineNumber,     // line number of error  
    LONG *pichCharPosition    // character position of error  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdwSourceContext`  
 [out] Адрес переменной, которая получает файл cookie, который идентифицирует контекст. Интерпретация этого параметра зависит от ведущего приложения.  
  
 `pulLineNumber`  
 [out] Адрес переменной, которая получает номер строки в исходном файле, где произошла ошибка.  
  
 `pichCharPosition`  
 [out] Адрес переменной, которая получает положение символа в строке, в котором произошла ошибка.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` в случае успешного выполнения или `E_FAIL` Если расположение не был получен.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)