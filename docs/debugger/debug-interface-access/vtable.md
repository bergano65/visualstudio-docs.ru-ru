---
title: "VTable | Microsoft Docs"
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
  - "VTable - символ"
  - "виртуальные таблицы"
ms.assetid: c8be6692-7d2a-4721-99d3-8e2e565bb8a1
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# VTable
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Таблица определяется на самом деле `SymTagVTable` символ.  
  
## Свойства  
 В следующей таблице показаны допустимые дополнительные свойства для данного типа символов.  
  
|Свойство.|Тип данных|Описание|  
|---------------|----------------|--------------|  
|[IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md)|`IDiaSymbol*`|Символ класса, имеющий это VTable.|  
|[IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md)|`DWORD`|Идентификатор родительского класса символов.|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` если класс VTable помечен как константа.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Символ включающего compiland.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Идентификатор словарного родительского символов.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Идентификатор индекса символа.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Возвращает `SymTagVTable` \(одно из  [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) значения\).|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Символ, VTable [VTableShape](../../debugger/debug-interface-access/vtableshape.md).|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Идентификатор типа символа.|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` если класс бесподстроечн VTable.|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` если класс VTable помечен как volatile.|  
  
## См. также  
 [Иерархия классов символьных типов](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [VTableShape](../../debugger/debug-interface-access/vtableshape.md)