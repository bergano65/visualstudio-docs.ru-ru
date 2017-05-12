---
title: "IActiveScript::InterruptScriptThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.InterruptScriptThread
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_InterruptScriptThread"
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::InterruptScriptThread
Прерывает выполнение выполняющегося потока скрипта \(приемника событий, немедленного выполнения или вызова макросов\).  Этот метод можно использовать для выполнения скриптов, который вставлен \(например, в бесконечном цикле\).  Он может быть вызван из потоков, не относящихся к базовому без привести к появлению выноски отличные от причины для размещения объектов или методу [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md).  
  
## Синтаксис  
  
```  
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### Параметры  
 `stidThread`  
 \[in\] идентификатор потока прерван или следующего специального идентификатора потока оценка:  
  
|Значение|Значение|  
|--------------|--------------|  
|SCRIPTTHREADID\_ALL|Все потоки.  Прерывание применитьо ко всему методов сценария выполняется в данный момент.  Обратите внимание, что если вызывающий объект не будет запрашивать, что скрипт отключен, следующий код сценария в скрипт причин события, которое будет запущен повторно путем вызова метода [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) с набором SCRIPTSTATE\_DISCONNECTED или пометить SCRIPTSTATE\_INITIALIZED.|  
|SCRIPTTHREADID\_BASE|Базовый поток. то есть поток, в котором был создан экземпляр обработчика сценариев.|  
|SCRIPTTHREADID\_CURRENT|Выполняющийся в данный момент поток.|  
  
 `pexcepinfo`  
 \[in\] адрес структуры `EXCEPINFO`, содержащий сведения об ошибке, которое должно быть отмечено в прерватьому скрипту.  
  
 `dwFlags`  
 \[in\] флаги, связанные с помощью параметра условие.  Может принимать одно из следующих значений.  
  
|Значение|Значение|  
|--------------|--------------|  
|SCRIPTINTERRUPT\_DEBUG|Если поддерживается, введите отладчик обработчика скриптов на текущий этап выполнения скрипта.|  
|SCRIPTINTERRUPT\_RAISEEXCEPTION|Если поддерживается языком обработчика скриптов, скрипту обработки исключения.  В противном случае метод скрипта прерывается и код ошибки возвращается вызывающему коду. то есть средство вызова источника событий или макроса.|  
  
## Возвращаемое значение  
 Возвращать одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|---------------------------|--------------|  
|`S_OK`|Успех.|  
|`E_INVALIDARG`|Аргумент был недопустимым.|  
|`E_POINTER`|Недопустимый указатель был определен.|  
|`E_UNEXPECTED`|Вызов не ожидался \(например, обработчик скриптов еще не был загружен или не был инициализирован\).|  
  
## См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)