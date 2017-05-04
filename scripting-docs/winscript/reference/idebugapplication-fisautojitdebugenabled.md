---
title: "IDebugApplication::FIsAutoJitDebugEnabled | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.FIsAutoJitDebugEnabled
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::FIsAutoJitDebugEnabled"
ms.assetid: 0551dd3b-e6eb-442a-8201-418f96fe62df
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::FIsAutoJitDebugEnabled
Определяет, если по требованию \(JIT\) отладчик зарегистрировать к основным приложениям автоматическ\- отладка тупым.  
  
## Синтаксис  
  
```  
BOOL FIsAutoJitDebugEnabled();  
```  
  
#### Параметры  
 Этот метод не принимает параметры.  
  
## Возвращаемое значение  
 Если метод завершается успешно и JIT отладчик зарегистрировать к основным приложениям автоматическ\- отладка тупым, то метод возвращает `TRUE`.  В противном случае возвращается значение `FALSE`.  
  
## Заметки  
 Этот метод определяет, если отладчик JIT зарегистрировать к основным приложениям автоматическ\- отладка тупым.  
  
## См. также  
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)