---
title: "PublicSymbol | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "символы данных [C++]"
  - "PublicSymbol - символ"
  - "глобальные функции [C++], как открытые символы"
ms.assetid: f8d33007-302d-4549-9dad-47fb33ea60b7
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# PublicSymbol
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

При создании исполняемого файла, то каждому символу \(public, как минимум, каждой глобальной функции и символе данных a\) `SymTagPublicSymbol` тег.  
  
## Свойства  
 В следующей таблице показаны свойства, которые являются допустимыми для данного типа символов.  
  
|Свойство.|Тип данных|Описание|  
|---------------|----------------|--------------|  
|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Часть смещения положения; дополнительные сведения см. в разделе [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Часть раздела расположения; дополнительные сведения см. в разделе [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_code](../../debugger/debug-interface-access/idiasymbol-get-code.md)|`BOOL`|`TRUE` если расположение символа в коде.|  
|[IDiaSymbol::get\_function](../Topic/IDiaSymbol::get_function.md)|`BOOL`|`TRUE` если символ функция.|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Длина этого символа в байтах.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Символ для глобальной области.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Идентификатор словарного родительского символов.|  
|[IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md)|`DWORD`|Открытые символы имеют статические расположения; дополнительные сведения см. в разделе [Местоположения символов](../../debugger/debug-interface-access/symbol-locations.md).|  
|[IDiaSymbol::get\_managed](../../debugger/debug-interface-access/idiasymbol-get-managed.md)|`BOOL`|`TRUE` если расположение символа в управляемом коде.|  
|[IDiaSymbol::get\_msil](../../debugger/debug-interface-access/idiasymbol-get-msil.md)|`BOOL`|`TRUE` если расположение символа в коде на языке MSIL.|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|Полностью декорированное имя символа.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Идентификатор индекса символа.|  
|[IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Относительное положение символа в пределах своего блок.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Возвращает `SymTagPublicSymbol` \(одно из  [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) значения\).|  
|[IDiaSymbol::get\_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|`BSTR`|Упрощенного имя символа.|  
|[IDiaSymbol::get\_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`BSTR`|Часть или все упрощенного имя символа.|  
  
## См. также  
 [Лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md)   
 [Местоположения символов](../../debugger/debug-interface-access/symbol-locations.md)