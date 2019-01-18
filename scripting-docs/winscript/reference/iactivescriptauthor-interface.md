---
title: Интерфейс IActiveScriptAuthor | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptAuthor interface
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd9d9c2a330ee72c6a843cd42586a09bb1d51e3c
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346375"
---
# <a name="iactivescriptauthor-interface"></a>Интерфейс IActiveScriptAuthor
Представляет создание служб, включая IntelliSense и параметры сортировки данных.  
  
 Помимо методов, наследуемых от `IUnknown`, `IActiveScriptAuthor` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Добавляет имя элемента корневого уровня в скрипт создания механизма пространства имен. Объект *элемент корневого уровня* — это объект, который может содержать свойства и методы, а, может также содержать источник события.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Добавляет сценарий кода в качестве дочернего элемента корневого уровня `IScriptNode` объекта. В узле полное имя сценария может иметь только два уровня.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Добавляет библиотеку типов в пространство имен для скрипта.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|Возвращает набор символов завершения для запрошенного завершения контекста.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Возвращает сценария, с указанными атрибутами.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|Возвращает тип сведений и положения привязки для заданного символа в блоке кода. Это предоставляет сведения для элемента, IntelliSense, глобальные списки и подсказки по параметрам.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|Возвращает сведения о языке.|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|Возвращает `IScriptNode` корень дерева автора скрипта.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Возвращает атрибуты текста скриптлета.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|Возвращает атрибуты текстового блока скрипта.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|Возвращает значение, указывающее, должен ли определенный символ фиксировать завершение операторов для приложения.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|Выполняет синтаксический анализ текста скрипта, добавляет текст в разработки скрипт создания ядра и создает `IScriptEntry` объект, соответствующий блок скрипта.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|Удаляет `NamedItem` объекта из пространства имен сценария разработки ядра.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|Удаляет библиотеку типов из скрипта создания пространства имен модуля.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы для создания активных скриптов](../../winscript/reference/active-script-authoring-interfaces.md)