---
title: Символы и теги символов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d2281a82926dabfde88b8d4bb9096f0e9624211
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738521"
---
# <a name="symbols-and-symbol-tags"></a>Символы и теги символов
Отладочная информация о скомпилированной программе хранится в файле базы данных программы (PDB) в виде символов, доступных с помощью API-интерфейсов SDK для доступа к интерфейсу отладки (DIA). Все символы имеют свойство [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) и [IDiaSymbol:: get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) . Свойство `symTag` указывает тип символа, определенного перечислением [перечисления симтаженум](../../debugger/debug-interface-access/symtagenum.md) . Свойство `symIndexId` — это `DWORD` значение, которое содержит уникальный идентификатор для каждого экземпляра символа.

 Символы также имеют свойства, которые могут указывать дополнительные сведения о символе, а также ссылки на другие символы, чаще всего это [IDiaSymbol:: get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) или [IDiaSymbol:: get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). При запросе свойства, содержащего ссылку, ссылка возвращается как объект [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) . Такие свойства всегда сопряжены с другим свойством с тем же именем, но с суффиксом "ID", например [IDiaSymbol:: get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) и [IDiaSymbol:: get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Таблицы в [расположениях символов](../../debugger/debug-interface-access/symbol-locations.md), [лексическая иерархия типов символов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)и [Иерархия классов типов символов](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) описывают свойства для каждого из различных видов символов. Эти свойства могут иметь релевантную информацию о других символах или ссылках на них. Поскольку свойства `*Id` представляют собой только числовые порядковые идентификаторы связанных с ними свойств, они пропускаются из дальнейших обсуждений. Они упоминаются только в том случае, если это необходимо для уточнения параметров.

 При попытке получить доступ к свойству, если ошибка не возникает и свойству символа было присвоено значение, метод Get свойства возвращает `S_OK`. Возвращаемое значение `S_FALSE` указывает, что свойство не является допустимым для текущего символа.

## <a name="in-this-section"></a>Содержание

[Местоположения символов](../../debugger/debug-interface-access/symbol-locations.md)

Описывает различные виды расположений, которые может содержать символ.

[Лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)

Описывает типы символов, которые формируют лексические иерархии, такие как файлы, модули и функции.

[Иерархия классов символьных типов](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)

Описывает типы символов, соответствующие различным языковым элементам, таким как классы, массивы и возвращаемые типы функций.

## <a name="see-also"></a>См. также

- [SDK для доступа к интерфейсу отладки](../../debugger/debug-interface-access/debug-interface-access-sdk.md)