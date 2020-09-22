---
title: Лексическая иерархия типов символов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e70b83046c41b13cb51324eb63e81b26a118a81f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842952"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Лексическая иерархия символьных типов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В следующей таблице показаны типы символов в лексической иерархии.  
  
## <a name="symbol-types"></a>Типы символов  
  
|Тип символа|Description|  
|-----------------|-----------------|  
|[Комментарий](../../debugger/debug-interface-access/annotation.md)|Задает расположение с заметками в коде программы.|  
|[Заблокировать](../../debugger/debug-interface-access/block.md)|Задает вложенные области в функциях.|  
|`Compiland`|Указывает объект, `compiland` связанный с exe-файлом.|  
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Указывает данные компилируемого объекта, которые могут потребовать загрузки дополнительных сведений о компилируемого объекта и, таким же, требуют издержек во время выполнения для получения.|  
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Указывает все дополнительные переменные среды, которые важны для компиляции компилируемого объекта.|  
|[Custom (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Задает определяемый пользователем символ.|  
|[Data (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Задает такие переменные как параметры, локальные переменные, глобальные переменные и члены класса.|  
|[Exe](../../debugger/debug-interface-access/exe.md)|Задает глобальную область данных; соответствует целому exe-или DLL-файлу.|  
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Задает функцию с определенной точкой, в которой должна быть завершена отладка.|  
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Указывает функцию с определенной точкой, с которой начинается отладка.|  
|[Function (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Указывает функцию.|  
|[Label (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Указывает расположение в программном коде.|  
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Задает внешний символ, который появляется при создании исполняемой программы.|  
|[Thunk](../../debugger/debug-interface-access/thunk.md)|Указывает `thunk` .|  
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Задает `namespace` идентификатор.|  
  
> [!NOTE]
> Дополнительные свойства символов могут быть доступны в зависимости от типа символа. Эти свойства перечислены в разделах, посвященных отдельным символам.  
  
## <a name="see-also"></a>См. также:  
 [Иерархия классов типов символов](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)   
 [Символы и теги символов](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
