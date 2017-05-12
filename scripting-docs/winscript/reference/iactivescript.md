---
title: "IActiveScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScript — интерфейс"
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript
Предоставляет методы, необходимые инициализировал обработчика скриптов.  Обработчик скриптов должен реализовать интерфейс `IActiveScript`.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Уведомляет обработчик скриптов сайта [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) предоставленного основным приложением.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Извлекает объект сайта, связанный с обработчиком скрипта Windows.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Устанавливает обработчик скриптов в указанное состояние.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Получает текущее состояние обработчика скриптов.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Вызывает обработчик скриптов, чтобы прервать любой текущий загруженный скрипт, сохранить его состояние и освобождение все указатели интерфейса его другим объектам, поэтому вставка состояние закрыть.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|Добавляет имя элемента корень\- уровня к пространству имен обработчика скриптов.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|Добавляет библиотеки типов в пространстве имен для скрипта.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|Извлекает интерфейс `IDispatch` для выполнения скрипта.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|Извлекает scripting\-обработчик\- указанный идентификатор выполняющегося в настоящее время потока.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Извлекает scripting\-обработчик\- указанный идентификатор потока, связанного с данным потоком Microsoft Win32.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|Получает текущее состояние потока скрипта.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|Прерывает выполнение выполняющегося потока скрипта.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|Клонирует текущий обработчик скриптов \(минус любое текущее состояние выполнения\), возвращая загруженный обработчик скриптов, который не имеет сайт в текущем потоке.|  
  
## См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)