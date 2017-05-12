---
title: "IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug"
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Уведомляет основное приложение о ошибках во время выполнения скрипта, если диспетчер процесса отладки не находит а так же в отладчике скрипта Time.  
  
 Для реализации отладчик в основном приложении необходимо обрабатывать [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md).  На основе действию пользователя, основное приложение может либо вложить отладчик и извлечение и возврат запуска отладчика в параметре OnScriptErrorDebug `pfEnterDebugger`.  Необходимо также реализовать этот интерфейс, чтобы получать уведомления об ошибках во время выполнения даже при отсутствии внешние отладчики, которые могут интерпретироваться отростчатым диспетчером отладка.  
  
## Синтаксис  
  
```  
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### Параметры  
 `pErrorDebug`  
 \[in\] ошибка, произошедшая во время выполнения.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 \[out\], следует ли вызывать [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) если пользователь решает продолжить без отладки.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Необходимо также реализовать этот интерфейс, чтобы получить уведомление.  
  
## См. также  
 [IActiveScriptSiteDebugEx — интерфейс](../../winscript/reference/iactivescriptsitedebugex-interface.md)