---
title: "Интерфейс IActiveScriptAuthor | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptAuthor — интерфейс"
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Интерфейс IActiveScriptAuthor
Представляет создании службы, включая IntelliSense и параметры сортировки сведения.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IActiveScriptAuthor` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Добавляет имя элемента корень\- уровня к скрипту разработка пространство имен обработчика.  *Элемент корень\- уровня* объект, который может содержать свойства и методы, и может также содержать источник события.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Добавляет сценарий кода как дочерний элемент корневого уровня объекта `IScriptNode`.  В основном приложении полное имя скрипта может быть только 2 уровня.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Добавляет библиотеки типов в пространстве имен для скрипта.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|Возвращает набор символов завершения для контекста выполнения.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Возвращает скрипт, который имеет указанные атрибуты.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|Извлечения сведений о типе и положения привязки для заданного символа в блоке кода.  Это предоставляет сведения для членов IntelliSense, глобальных списков и советы по параметра.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|Возвращает сведения о языке.|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|Возвращает корневой элемент дерева `IScriptNode` скрипта автора.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Возвращает атрибуты текст сценария.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|Возвращает атрибуты текста блока скрипта.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|Возвращает значение, указывающее, должен ли заданный символ фиксировать завершение выписки приложением.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|Анализирует текст скрипта, добавляет текст в разработке скрипту создание обработчика и создает объект `IScriptEntry`, соответствующий блок скрипта.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|Удаляет объект `NamedItem` из пространства имен сценария создания обработчика.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|Удаляет библиотеку типов из скрипта создания пространство имен обработчика.|  
  
## См. также  
 [Интерфейсы для создания активных скриптов](../../winscript/reference/active-script-authoring-interfaces.md)