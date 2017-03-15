---
title: "FunctionType | Microsoft Docs"
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
  - "сигнатура функции"
  - "FunctionType - символ"
ms.assetid: 646a07e7-9d4f-4e21-95e3-3e403cdd4843
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# FunctionType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Каждая уникально подписи функции определяется a `SymTagFunctionType` символ.  Каждый параметр определен как символ дочернего элемента класса a `SymTagFunctionArgType` тег.  
  
## Свойства  
 В следующей таблице показаны допустимые дополнительные свойства для данного типа символов.  
  
|Свойство.|Тип данных|Описание|  
|---------------|----------------|--------------|  
|[IDiaSymbol::get\_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)|`DWORD`|Одно из значений  [Перечисление CV\_call\_e](../../debugger/debug-interface-access/cv-call-e.md).|  
|[IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md)|`IDiaSymbol*`|Класс которого эта функция \(или\) элемент.|  
|[IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md)|`DWORD`|Идентификатор родительского класса символов.|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` если функция помечена как константа.|  
|[IDiaSymbol::get\_count](../Topic/IDiaSymbol::get_count.md)|`DWORD`|Число параметров в функции.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Символ включающего compiland.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Идентификатор словарного родительского символов.|  
|[IDiaSymbol::get\_objectPointerType](../../debugger/debug-interface-access/idiasymbol-get-objectpointertype.md)|`IDiaSymbol*`|Тип указателя объекта метода \("this"\).|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Идентификатор индекса символа.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Возвращает `SymTagFunctionType` \(одно из  [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) значения\).|  
|[IDiaSymbol::get\_thisAdjust](../../debugger/debug-interface-access/idiasymbol-get-thisadjust.md)|`LONG`|Этот логический "" регулятора для метода.|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Символ для типа возвращаемого значения.|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Идентификатор типа символа.|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` если функция бесподстроечна.|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` если функция помечена как volatile.|  
  
## См. также  
 [Иерархия классов символьных типов](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [Перечисление CV\_access\_e](../../debugger/debug-interface-access/cv-access-e.md)   
 [FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)