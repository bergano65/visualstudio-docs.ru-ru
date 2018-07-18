---
title: Интерфейс IActiveScriptAuthor | Документы Microsoft
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
ms.openlocfilehash: 37abb356ab24d64a05a1f1209809d63e2f55e228
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645774"
---
# <a name="iactivescriptauthor-interface"></a>Интерфейс IActiveScriptAuthor
Представляет разработки служб, включая IntelliSense и параметры сортировки данных.  
  
 Помимо методов, наследуемых от `IUnknown`, `IActiveScriptAuthor` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Добавляет имя элемента на корневом уровне скрипт создания механизма пространства имен. Объект *корневой элемент* — это объект, содержащую свойства и методы, а также может содержать источник события.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Добавляет код пользователи в качестве дочернего элемента корневого уровня `IScriptNode` объекта. В узле полное имя сценариев могут иметь только двух уровней.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Добавляет библиотеку типов в пространство имен для скрипта.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|Возвращает набор символов завершения для завершения запрошенной контекста.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Возвращает сценарий, который с указанными атрибутами.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|Возвращает введите сведения и позиций привязки для заданного символа в блок кода. Это дает сведения для элемента, IntelliSense, глобальных списков и подсказки по параметрам.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|Возвращает сведения о языке.|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|Возвращает `IScriptNode` корень дерева скрипт автора.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Возвращает атрибуты текста пользователи.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|Возвращает атрибуты текстового блока скрипта.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|Возвращает значение, указывающее, следует ли определенный символ зафиксировать завершение операторов для приложения.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|Выполняет синтаксический анализ текста сценария, добавляет текст в разработки скрипт создания ядра и создает `IScriptEntry` объект, соответствующий блок сценария.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|Удаляет `NamedItem` объекта из пространства имен, модуль создания скрипта.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|Удаляет библиотеку типов из скрипта создания engine пространства имен.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы для создания активных скриптов](../../winscript/reference/active-script-authoring-interfaces.md)