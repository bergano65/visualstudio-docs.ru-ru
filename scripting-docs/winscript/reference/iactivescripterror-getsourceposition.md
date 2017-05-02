---
title: "IActiveScriptError::GetSourcePosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptError.GetSourcePosition
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptError_GetSourcePosition"
ms.assetid: ae9b26b1-82a7-4645-9686-3261d8248664
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError::GetSourcePosition
Извлекает местоположение в исходном коде, где произошла ошибка, пока обработчик скриптов выполняется скрипт.  
  
## Синтаксис  
  
```  
HRESULT GetSourcePosition(  
    DWORD *pdwSourceContext,  // context cookie  
    ULONG *pulLineNumber,     // line number of error  
    LONG *pichCharPosition    // character position of error  
);  
```  
  
#### Параметры  
 `pdwSourceContext`  
 \[out\] адрес переменной, которая получает файл cookie, который определяет контекст.  Интерпретация зависит от параметра ведущее приложение.  
  
 `pulLineNumber`  
 \[out\] адрес переменной, которая возвращает номер линии в исходном файле, где произошла ошибка.  
  
 `pichCharPosition`  
 \[out\] адрес переменной, которая возвращает позицию знака в линии, в котором произошла ошибка.  
  
## Возвращаемое значение  
 Возвращает `S_ОК`, если успешно или `E_FAIL`, если расположение не было восстановитьо.  
  
## См. также  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)