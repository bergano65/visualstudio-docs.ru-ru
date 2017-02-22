---
title: "Символы и теги символов | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "символы [пакет SDK для доступа к интерфейсу отладки]"
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Символы и теги символов
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Отладочная информация о программе компилированной хранятся в файле базы данных программы \(pdb\) как символы, которые доступны с помощью api\-интерфейса пакету SDK для доступа к интерфейсу отладки \(DIA\).  Все символы имеют a [IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md) и a  [IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) свойство.  `symTag` свойство указывает символьный тип в соответствии  [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) перечисление.  `symIndexId` свойство a  `DWORD` значение, содержащее уникальный идентификатор экземпляра для каждого символа.  
  
 Символы также имеют свойства, которые могут определять дополнительные сведения о символе, а также ссылки на другие символы, чаще всего a [IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) OR  [IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md).  При запросе свойство, содержащее ссылку, ссылка возвращается как [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объект.  Такие свойства всегда связыванны другим свойством с одинаковыми именами, но suffixed с "идентификатором", например [IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) и  [IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md).  Таблицы в пределах [Местоположения символов](../../debugger/debug-interface-access/symbol-locations.md)"  [Лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)и  [Иерархия классов символьных типов](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) конспектируйте свойства для каждого из различных типов символов.  Эти свойства могут иметь необходимые сведения о или ссылки на другие символы.  Поскольку `*Id` свойства \- это числовые идентификаторы используются их связанных свойств, их из более дополнительных обсуждений.  Они ссылаются на только тогда, когда для пояснения параметра.  
  
 При попытке доступа к свойству, если ошибка не происходит и присвоенное свойству символа значение, свойство получает метод "get" `S_OK`.  Возвращаемое значение  `S_FALSE` указывает, что свойство недопустимо для текущего символов.  
  
## В этом подразделе  
 [Местоположения символов](../../debugger/debug-interface-access/symbol-locations.md)  
 Описывает различные типы расположения может содержать символ.  
  
 [Лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 Описывает типы символов, которые формируют лексических иерархии в виде файлов, модули и функции.  
  
 [Иерархия классов символьных типов](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 Описывает типы символов, которые соответствуют разным элементам языка, как классы, массивы и возвращаемые типы функций.  
  
## См. также  
 [SDK для доступа к интерфейсу отладки](../../debugger/debug-interface-access/debug-interface-access-sdk.md)