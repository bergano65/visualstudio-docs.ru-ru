---
title: "IDebugApplication::HandleRuntimeError | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.HandleRuntimeError
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::HandleRuntimeError"
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::HandleRuntimeError
Вынуждает текущий поток отключения и отправляет уведомление ошибок в интегрированной среде разработки отладчика.  
  
## Синтаксис  
  
```  
HRESULT HandleRuntimeError(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   IActiveScriptSite*        pScriptSite,  
   BREAKRESUMEACTION*        pbra,  
   ERRORRESUMEACTION*        perra,  
   BOOL*                     pfCallOnScriptError  
);  
```  
  
#### Параметры  
 `pErrorDebug`  
 \[in\] ошибка, произошедшая.  
  
 `pScriptSite`  
 \[in\] сайт сценария потока.  
  
 `pbra`  
 \[out\] действие, выполняемое при возобновлении приложения отладчик.  
  
 `perra`  
 \[out\] действие, выполняемое при возобновлении приложения отладчик если ошибка.  
  
 `pfCallOnScriptError`  
 \[out\] `TRUE` пометить, если обработчик должен вызывает метод `IActiveScriptSite::OnScriptError`.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Обработчик языка вызывает этот метод в контексте потока, который вызывает ошибку во время выполнения.  Этот метод вызывает текущий поток отключения и отправляет уведомление об ошибке для отправки в интегрированной среде разработки отладчика.  Когда интегрированная среда разработки отладчика, откуда приложение извлечения данного метода с действием, которые нужно выполнить.  
  
> [!NOTE]
>  При ошибке во время выполнения, обработчик языка может быть вызван потоком для выполнения таких задач, как перечисляет кадры стека или вычисляет выражения.  
  
## См. также  
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Интерфейс IActiveScriptErrorDebug](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)   
 [Перечисление BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)   
 [Перечисление ERRORRESUMEACTION](../../winscript/reference/errorresumeaction-enumeration.md)