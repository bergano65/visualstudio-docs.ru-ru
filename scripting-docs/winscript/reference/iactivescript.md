---
title: "IActiveScript | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScript interface
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68d91a7ad91364d0c2133150d76cdb221929b16b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescript"></a>IActiveScript
Предоставляет методы, необходимые для инициализации обработчика скриптов. Необходимо реализовать обработчик скриптов `IActiveScript` интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Уведомляет обработчик скриптов для [iactivescriptsite —](../../winscript/reference/iactivescriptsite.md) сайта, предоставленный средой размещения.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Извлекает объект узла, связанный с обработчиком сценариев Windows.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Помещает обработчик скриптов в указанном состоянии.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Извлекает текущее состояние обработчика сценариев.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Вызывает обработчик скриптов для прерывания любой сценарий, текущая загруженная, теряют свое состояние и освободить все указатели на интерфейс, он имеет другим объектам, таким образом, введя состояние closed.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|Добавляет имя элемента корневого уровня пространства имен обработчика скриптов.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|Добавляет библиотеку типов в пространство имен для скрипта.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|Извлекает `IDispatch` интерфейс для выполняемого сценария.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|Извлекает определенный сценариев ядра-идентификатор для текущего потока.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Извлекает определенный сценариев ядра-идентификатор потока, связанного с данной потоком Microsoft Win32.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|Извлекает текущее состояние потока сценария.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|Прерывает выполнение выполняющийся поток скрипта.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|Клонирует текущий обработчик скриптов (минус любое текущее состояние выполнения), возврат загрузить обработчик скриптов, у которой нет сайт в текущем потоке.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)