---
title: Символы и теги символов | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 72f4cb4b6ed35e880e1cb26980420f4e951ffc16
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="symbols-and-symbol-tags"></a>Символы и теги символов
Отладочной информации о скомпилированная программа хранится в PDB-файл программы, как символы, которые доступны с помощью API пакета SDK для отладки Interface Access (DIA). Все символы имеют [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) и [IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) свойство. `symTag` Свойство указывает тип символа, в соответствии с определением [SymTagEnum-перечисление](../../debugger/debug-interface-access/symtagenum.md) перечисления. `symIndexId` Свойство `DWORD` значение, содержащее уникальный идентификатор для каждого вхождения символа.  
  
 Символы также имеют свойства, которые можно указать дополнительные сведения о символов, а также ссылки на другие символы, чаще всего [IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) или [IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). Возвращается при запросе свойство, которое содержит ссылку на ссылку в виде [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объекта. Такие свойства всегда сопоставляются с другим свойством с тем же именем, но с суффиксом «Идентификатор», например, [IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) и [IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Таблицы в [расположения символов](../../debugger/debug-interface-access/symbol-locations.md), [лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md), и [класс иерархия символьных типов](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) структуры свойства для каждого из различных типов из символы. Эти свойства могут иметь актуальную информацию о или ссылки на другие символы. Поскольку `*Id` свойств являются просто числовые идентификаторы порядковый номер, их связанных свойств, они исключаются из дальнейшего обсуждения. Они называются только в том случае, если для параметра дополнительной информации.  
  
 При попытке получить доступ к свойству, если ошибка не возникает и свойство символ назначено значение, свойство «получить» возвращает метод `S_OK`. Возвращаемое значение `S_FALSE` указывает, что свойство не является допустимым для текущий символ.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Местоположения символов](../../debugger/debug-interface-access/symbol-locations.md)  
 Описывает различные расположения, которые могут иметь символ.  
  
 [Лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 Описывает типы символов, формирующие лексической иерархии, такие как файлы, модули и функции.  
  
 [Иерархия классов символьных типов](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 Описывает типы символов, которые соответствуют различные языковые элементы, такие как классы, массивы и функции возвращают типы.  
  
## <a name="see-also"></a>См. также  
 [SDK для доступа к интерфейсу отладки](../../debugger/debug-interface-access/debug-interface-access-sdk.md)