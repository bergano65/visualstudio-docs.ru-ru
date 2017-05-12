---
title: "IActiveScriptSite::OnScriptError | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnScriptError
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnScriptError"
ms.assetid: 5c9c85cc-21ad-4232-be83-a24cc7570108
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnScriptError
Уведомляет основное приложение о том, что ошибка произошла во время запуска выполнения обработчика скриптов.  
  
## Синтаксис  
  
```  
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### Параметры  
 `pase`  
 \[in\] адрес интерфейса [IActiveScriptError](../../winscript/reference/iactivescripterror.md) объекта ошибки.  Основное приложение может использовать этот интерфейс для получения сведений об ошибках выполнения.  
  
## Возвращаемое значение  
 Возвращает `S_ОК` если ошибка была правильно, которым регулируется или OLE, указанный код ошибки, в противном случае.  
  
## См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)