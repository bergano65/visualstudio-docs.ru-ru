---
title: "IDebugApplication::StartDebugSession | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.StartDebugSession
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::StartDebugSession"
ms.assetid: 737f8424-bbcf-473f-9cf1-6601b9aa250d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::StartDebugSession
Запуск отладчика по умолчанию интегрированная среда разработки \(ide\) и атташеы сеанс отладки к этому приложению, если она еще не вложитьо.  
  
## Синтаксис  
  
```  
HRESULT StartDebugSession();  
```  
  
#### Параметры  
 Этот метод не принимает параметры.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод используется для реализации JIT\-отладка.  
  
## См. также  
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)