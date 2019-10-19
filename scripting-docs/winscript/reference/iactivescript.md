---
title: IActiveScript | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScript interface
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7a33db2bcbcb356a508fec2e6bc5449a899a1299
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577234"
---
# <a name="iactivescript"></a>IActiveScript
Предоставляет методы, необходимые для инициализации обработчика скриптов. Обработчик скриптов должен реализовывать интерфейс `IActiveScript`.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Информирует обработчик скриптов сайта [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) , предоставленного узлом.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Извлекает объект сайта, связанный с обработчиком сценариев Windows.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Помещает обработчик скриптов в указанное состояние.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Извлекает текущее состояние обработчика скриптов.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Заставляет обработчик скриптов отменять любой загруженный скрипт, терять его состояние и освобождать все указатели интерфейса, которые он имеет, на другие объекты, тем самым выполняя вход в закрытое состояние.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|Добавляет имя элемента корневого уровня в пространство имен обработчика скриптов.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|Добавляет библиотеку типов в пространство имен для скрипта.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|Извлекает интерфейс `IDispatch` для выполняющегося скрипта.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|Извлекает идентификатор, определяемый обработчиком сценариев, для выполняющегося в данный момент потока.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Извлекает идентификатор, определяемый обработчиком сценариев, для потока, связанного с заданным потоком Microsoft Win32.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|Извлекает текущее состояние потока скрипта.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|Прерывает выполнение выполняющегося потока скрипта.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|Копирует текущий обработчик скриптов (за исключением любого текущего состояния выполнения), возвращая загруженный обработчик скриптов, не имеющий сайта в текущем потоке.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)