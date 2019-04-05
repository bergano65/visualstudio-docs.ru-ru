---
title: Символы и теги символов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 625752125d3c68e9f03afd41cd549995fbc3272e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58980534"
---
# <a name="symbols-and-symbol-tags"></a>Символы и теги символов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Отладочной информации о скомпилированную программу хранится в PDB-файл программы, как символы, которые доступны с помощью API пакета SDK для отладки Interface Access (DIA). Все символы имеют [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) и [IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) свойство. `symTag` Свойство указывает типа символа, в соответствии с определением [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) перечисления. `symIndexId` Свойство `DWORD` значение, содержащее уникальный идентификатор для каждого вхождения символа.  
  
 Символы также имеют свойства, которые можно указать дополнительные сведения о символ, а также ссылки на другие символы, чаще всего [IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) или [IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). При запросе свойство, которое содержит ссылку, возвращается в виде ссылки [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объекта. Такие свойства всегда сопоставляются с другим свойством с одинаковыми именами и суффиксом, содержащим «Id», например, [IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) и [IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Таблицы в [расположения символов](../../debugger/debug-interface-access/symbol-locations.md), [лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md), и [класс иерархия символьных типов](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) структуры свойства для каждого из различных типов объекта символы. Эти свойства могут иметь соответствующие сведения о или ссылки на другие символы. Так как `*Id` свойства — это просто числовые идентификаторы порядковый номер их связанных свойств, они исключаются из дальнейшего обсуждения. Они известны только в том случае, при необходимости для получения параметра.  
  
 При попытке доступа к свойству, если ошибка не возникает и свойство символ назначено значение, свойство «получить» возвращает метод `S_OK`. Возвращаемое значение `S_FALSE` указывает, что свойство не является допустимым для текущего символа.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Местоположения символов](../../debugger/debug-interface-access/symbol-locations.md)  
 Описывает различные виды расположений, которые могут иметь символ.  
  
 [Лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 Описывает типы символов, которые образуют лексические иерархии, такие как файлы, модули и функции.  
  
 [Иерархия классов символьных типов](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 Описывает типы символов, которые соответствуют разные языковые элементы, такие как классы, массивы и функции возвращают типы.  
  
## <a name="see-also"></a>См. также  
 [SDK для доступа к интерфейсу отладки](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
