---
title: Лексическая иерархия символьных типов | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 58c4ef49cb7eabae7608ce417e4f3d5ef99a8284
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Лексическая иерархия символьных типов
Следующая таблица показывает символьных типов в иерархии лексической.  
  
## <a name="symbol-types"></a>Типы символов  
  
|Тип символа|Описание|  
|-----------------|-----------------|  
|[Комментарий](../../debugger/debug-interface-access/annotation.md)|Указывает размещение заметками в программном коде.|  
|[Block](../../debugger/debug-interface-access/block.md)|Задает вложенные области в функции.|  
|`Compiland`|Указывает `compiland` ссылкой на файл .exe.|  
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Указывает единицу компиляции данные, может потребоваться загрузка дополнительных компилируемого объекта сведений о и таким образом создают во время выполнения издержки для получения.|  
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Указывает все дополнительные переменные окружения значимым для компиляции компилируемого объекта.|  
|[Custom (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Указывает определяемого пользователем символа.|  
|[Data (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Указывает таких переменных, как параметры, локальные переменные, глобальные переменные и члены класса.|  
|[Exe](../../debugger/debug-interface-access/exe.md)|Указывает глобальной области данных. соответствует всего файла .exe или .dll.|  
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Указывает функцию, которая имеет определенные точки какие отладки является до конца.|  
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Указывает функцию, которая имеет определенные точки какие отладки является начинается.|  
|[Function (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Задает функцию.|  
|[Label (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Указывает расположение, в программном коде.|  
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Указывает внешний символ, который отображается при построении исполняемой программы.|  
|[Thunk](../../debugger/debug-interface-access/thunk.md)|Указывает `thunk`.|  
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Указывает `namespace`идентификатор.|  
  
> [!NOTE]
>  Дополнительные свойства могут быть доступны в зависимости от типа символа. Эти свойства перечислены в разделах отдельный символ.  
  
## <a name="see-also"></a>См. также  
 [Иерархия классов символьных типов](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)   
 [Символы и теги символов](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)