---
title: "BaseClass | Microsoft Docs"
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
  - "определяемые пользователем типы, базовые классы"
  - "BaseClass - символ"
  - "базовые классы, определяемые пользователем типы"
ms.assetid: 9375ca35-cb91-45f5-8903-7344ee4528e8
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# BaseClass
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Каждый базовый класс для символов пользовательского типа \(udt\) определяется с дочерним элементом `SymTagBaseClass` тег.  [IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) свойство содержит символ для основного определяемого пользователем типа, и все свойства основного определяемые пользователем типы доступны как часть этого символа BaseClass.  
  
## Свойства  
 В следующей таблице показаны допустимые дополнительные свойства для данного типа символов.  
  
|Свойство.|Тип данных|Описание|  
|---------------|----------------|--------------|  
|[IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Модификатор доступа к этому базовому классу.  Одно из значений [Перечисление CV\_access\_e](../../debugger/debug-interface-access/cv-access-e.md).|  
|[IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md)|`IDiaSymbol*`|Символ включающего класса \(если есть\).|  
|[IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md)|`DWORD`|Идентификатор родительского класса символов.|  
|[IDiaSymbol::get\_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|`BOOL`|`TRUE` если базовый класс содержит конструктор.|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` если базовый класс помечен как const.|  
|[IDiaSymbol::get\_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|`BOOL`|`TRUE` если базовый класс содержит оператор присваивания.|  
|[IDiaSymbol::get\_hasCastOperator](../Topic/IDiaSymbol::get_hasCastOperator.md)|`BOOL`|`TRUE` если базовый класс содержит оператор приведения.|  
|[IDiaSymbol::get\_hasNestedTypes](../Topic/IDiaSymbol::get_hasNestedTypes.md)|`BOOL`|`TRUE` если базовый класс содержит вложенные типы.|  
|[IDiaSymbol::get\_indirectVirtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-indirectvirtualbaseclass.md)|`BOOL`|`TRUE` если базовый класс косвенн.|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`DWORD`|Длина этого базового класса в байтах.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Символ включающего compiland.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Идентификатор словарного родительского символов.|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|Имя базового класса.|  
|[IDiaSymbol::get\_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|`BOOL`|`TRUE` если базовый класс является вложенным.|  
|[IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Смещение subobject, представляющий базовый класс внутри структуры.|  
|[IDiaSymbol::get\_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|`BOOL`|`TRUE` если базовый класс содержит все перегруженные операторы.|  
|[IDiaSymbol::get\_packed](../Topic/IDiaSymbol::get_packed.md)|`BOOL`|`TRUE` если базовый класс упаковыванн.|  
|[IDiaSymbol::get\_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|`BOOL`|`TRUE` если базовый класс отображается в nonglobal область.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Идентификатор индекса символа.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Возвращает `SymTagBaseClass` \(одно из  [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) значения\).|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Символ для базового класса [UDT](../../debugger/debug-interface-access/udt.md).|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Идентификатор типа символа.|  
|[IDiaSymbol::get\_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|`DWORD`|Значение [Перечисление UdtKind](../../debugger/debug-interface-access/udtkind.md).|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` если базовый класс бесподстроечн.|  
|[IDiaSymbol::get\_virtualBaseClass](../Topic/IDiaSymbol::get_virtualBaseClass.md)|`BOOL`|`TRUE` если базовый класс виртуальным.|  
|[IDiaSymbol::get\_virtualBaseDispIndex](../Topic/IDiaSymbol::get_virtualBaseDispIndex.md)|`DWORD`|Индекс в виртуальном базовую таблицу смещения.|  
|[IDiaSymbol::get\_virtualBasePointerOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbasepointeroffset.md)|`LONG`|Смещение виртуального базового указателя.|  
|[IDiaSymbol::get\_virtualBaseTableType](../Topic/IDiaSymbol::get_virtualBaseTableType.md)|`IDiaSymbol*`|Тип фактически указателя базовой таблицы.|  
|[IDiaSymbol::get\_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|`IDiaSymbol*`|Символ, описывающий тип фактически таблицы для данного базового класса.|  
|[IDiaSymbol::get\_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|`DWORD`|Идентификатор виртуального символов фигуры таблицы.|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` если базовый класс помечен как volatile.|  
  
## См. также  
 [Иерархия классов символьных типов](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [UDT](../../debugger/debug-interface-access/udt.md)