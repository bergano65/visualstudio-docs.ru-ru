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
ms.openlocfilehash: 5b7e3a0172a798eab9a743f446dff3d339a785b2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151003"
---
# <a name="iactivescript"></a>IActiveScript
Предоставляет методы, необходимые для инициализации обработчика скриптов. Обработчик скриптов должен реализовать `IActiveScript` интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Информирует обработчик сценариев из [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) сайта, предоставленный средой размещения.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Извлекает объект узла, связанный с обработчик скриптов Windows.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Помещает обработчик скриптов в указанном состоянии.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Возвращает текущее состояние обработчика сценариев.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Вызывает обработчик скриптов отказаться от любого текущего загруженного скрипта, теряют свое состояние и освободить все указатели на интерфейс, он имеет к другим объектам, таким образом ввод закрытом состоянии.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|Добавляет имя элемента корневого уровня пространства имен обработчика сценариев.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|Добавляет библиотеку типов в пространство имен для скрипта.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|Извлекает `IDispatch` интерфейс для выполняемого скрипта.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|Извлекает определенный сценариев ядра-идентификатор для текущего потока.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Извлекает определенный сценариев ядра-идентификатор для потока, связанного с данного потока Microsoft Win32.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|Возвращает текущее состояние потока скрипта.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|Прерывает выполнение выполняющийся поток скрипта.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|Клонирует текущий обработчик скриптов (минус любое текущее состояние выполнения), возвращая загружен обработчик скриптов, который у нет сайта в текущем потоке.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)