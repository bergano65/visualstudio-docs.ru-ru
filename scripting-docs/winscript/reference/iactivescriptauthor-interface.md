---
title: Интерфейс Иактивескриптаусор | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: ed0734fa48d58a5eae779c75c838c09215ed60a0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576159"
---
# <a name="iactivescriptauthor-interface"></a>Интерфейс IActiveScriptAuthor
Представляет службы разработки, включая IntelliSense и параметры сортировки данных.  
  
 В дополнение к методам, унаследованным от `IUnknown`, интерфейс `IActiveScriptAuthor` предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Добавляет имя элемента корневого уровня в пространство имен механизма разработки скриптов. *Элемент корневого уровня* — это объект, который может содержать свойства и методы, а также может содержать источник события.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Добавляет код скриптлет в качестве дочернего объекта `IScriptNode` корневого уровня. В узле полное имя скриптлет может иметь только два уровня.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Добавляет библиотеку типов в пространство имен для скрипта.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|Возвращает набор символов завершения для запрошенного контекста завершения.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Возвращает скриптлет с указанными атрибутами.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|Возвращает сведения о типе и позиции привязки для заданного символа в блоке кода. Это предоставляет сведения для элементов IntelliSense, глобальных списков и советов по параметрам.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|Возвращает сведения о языке.|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|Возвращает `IScriptNode` корень дерева скрипта автора.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Возвращает атрибуты текста объекта скриптлет.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|Возвращает атрибуты текста блока скрипта.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|Возвращает значение, указывающее, должен ли данный символ зафиксировать завершение операторов приложением.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|Анализирует текст скрипта, добавляет текст в подсистему создания скриптов разработки и создает объект `IScriptEntry`, соответствующий блоку скрипта.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|Удаляет объект `NamedItem` из пространства имен обработчика создания скриптов.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|Удаляет библиотеку типов из пространства имен обработчика создания скриптов.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы для создания активных скриптов](../../winscript/reference/active-script-authoring-interfaces.md)