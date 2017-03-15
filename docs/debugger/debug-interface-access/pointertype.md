---
title: "PointerType | Microsoft Docs"
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
  - "PointerType - символ"
ms.assetid: 67228681-7345-4537-8af3-93806803ee96
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# PointerType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Каждый указатель определяется a `SymTagPointerType` символ.  
  
## Свойства  
 В следующей таблице показаны допустимые дополнительные свойства для данного типа символов.  
  
|Свойство.|Тип данных|Описание|  
|---------------|----------------|--------------|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` если указатель помечен как константа.|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Размер в байтах для указателя.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Символ заключать [Compiland](../../debugger/debug-interface-access/compiland.md).|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Идентификатор словарного родительского символов.|  
|[IDiaSymbol::get\_reference](../Topic/IDiaSymbol::get_reference.md)|`BOOL`|`TRUE` если указатель является ссылочным типом.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Идентификатор индекса символа.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Возвращает `SymTagPointerType` \(одно из  [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) значения\).|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Символ целевого объекта указателя.|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Идентификатор типа символа.|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` если указатель бесподстроечн.|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` если указатель помечен как volatile.|  
  
## См. также  
 [Иерархия классов символьных типов](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)