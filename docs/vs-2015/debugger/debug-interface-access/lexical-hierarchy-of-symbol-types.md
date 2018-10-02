---
title: Лексическая иерархия символьных типов | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d807841429a722f31f3aecdc08f1a0972b05378
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560053"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Лексическая иерархия символьных типов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [лексическая иерархия символьных типов](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/lexical-hierarchy-of-symbol-types).  
  
Следующая таблица показывает символьных типов в иерархии лексические.  
  
## <a name="symbol-types"></a>Типы символов  
  
|Тип символа|Описание|  
|-----------------|-----------------|  
|[Комментарий](../../debugger/debug-interface-access/annotation.md)|Задает расположение с заметками в программном коде.|  
|[Block](../../debugger/debug-interface-access/block.md)|Задает вложенные области в функции.|  
|`Compiland`|Указывает `compiland` ссылкой на файл .exe.|  
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Указывает данные единице компиляции, может требовать загрузка сведений о дополнительной единице компиляции и таким образом взимается во время выполнения издержки для получения.|  
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Указывает все дополнительные переменные среды значимым для компиляции единице компиляции.|  
|[Custom (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Указывает определяемого пользователем символа.|  
|[Data (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Задает таких переменных в качестве параметров, локальных переменных, глобальных переменных и членов класса.|  
|[Exe](../../debugger/debug-interface-access/exe.md)|Указывает глобальной области данных. соответствует весь файл .exe или .dll.|  
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Указывает функцию, которая содержит это определенная точка в какие Отладка – это.|  
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Указывает функцию, которая содержит это определенная точка в какие отладки — чтобы начать.|  
|[Function (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Задает функцию.|  
|[Label (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Задает расположение в коде программы.|  
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Указывает внешний символ, появившемся при построении исполняемой программы.|  
|[Thunk](../../debugger/debug-interface-access/thunk.md)|Указывает `thunk`.|  
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Указывает `namespace`идентификатор.|  
  
> [!NOTE]
>  Дополнительные свойства могут быть доступны в зависимости от типа символа. Эти свойства перечислены в разделах отдельных символов.  
  
## <a name="see-also"></a>См. также  
 [Иерархия классов символьных типов](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)   
 [Символы и теги символов](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)



