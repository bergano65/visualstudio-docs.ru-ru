---
title: "IActiveScriptError::GetSourcePosition | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptError.GetSourcePosition
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptError_GetSourcePosition
ms.assetid: ae9b26b1-82a7-4645-9686-3261d8248664
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d63310a8ba5cfda39d48a482eaf7c345cd492adc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescripterrorgetsourceposition"></a>IActiveScriptError::GetSourcePosition
Извлекает расположение в исходном коде, где произошла ошибка обработчика скриптов был запущен сценарий.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 [out] Адрес переменной, которая получает положение символа в строке, в которой произошла ошибка.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` в случае успешного выполнения или `E_FAIL` Если расположение не был извлечен.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)