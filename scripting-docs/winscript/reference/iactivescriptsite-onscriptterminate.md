---
title: "IActiveScriptSite::OnScriptTerminate | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.OnScriptTerminate
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_OnScriptTerminate"
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::OnScriptTerminate
Уведомляет основное приложение о том, что одно выполнение скриптов.  
  
## Синтаксис  
  
```  
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### Параметры  
 `pvarResult`  
 \[in\] адрес переменной, содержащей результат скрипта или `NULL` если скрипт не дал нет.  
  
 `pexcepinfo`  
 \[in\] адрес структуры `EXCEPINFO`, содержащий данные об исключении, если скрипт был завершен или `NULL`, если исключение не было создано.  
  
## Возвращаемое значение  
 Возвращает значение `S_OK` в случае успеха.  
  
## Заметки  
 Обработчик скриптов вызывает этот метод прежде чем выполнить вызов метода [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) с набором SCRIPTSTATE\_INITIALIZED, пометить.  Этот метод может использоваться для возвращения состояние и результаты выполнения на узле.  Обратите внимание, что многие языки скриптов, которые основаны на тонуть событиях из основного приложения, имеющие жизненные точки, определенные основным приложением.  В этом случае этот метод не может никогда не должен вызываться.  
  
## См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)