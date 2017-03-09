---
title: "Function (SDK для доступа к интерфейсу отладки) | Microsoft Docs"
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
  - "Function - символ"
ms.assetid: 458dc91c-b78b-4427-84f4-615d89e26760
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Function (SDK для доступа к интерфейсу отладки)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Каждая функция определяется a `SymTagFunction` символ.  
  
## Свойства  
 В следующей таблице показаны свойства, которые являются допустимыми для данного типа символов.  
  
|Свойство.|`Data type`|Описание|  
|---------------|-----------------|--------------|  
|[IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Одно из значений  [Перечисление CV\_access\_e](../../debugger/debug-interface-access/cv-access-e.md), если функция функцию\-член.|  
|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Часть смещения положения; дополнительные сведения см. в разделе [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Часть раздела расположения; дополнительные сведения см. в разделе [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md)|`IDiaSymbol*`|Символ для класса, если функция функцию\-член.|  
|[IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md)|`DWORD`|Идентификатор родительского класса символов.|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` если функция помечена как константа.|  
|[IDiaSymbol::get\_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` если функция использует пользовательское соглашение о вызове \(только в пакет SDK для доступа к интерфейсу отладки V8.0 или более поздней версии\).|  
|[IDiaSymbol::get\_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` если функция выполняет дальше, возвращенное \(только в пакет SDK для доступа к интерфейсу отладки V8.0 или более поздней версии\).|  
|[IDiaSymbol::get\_hasAlloca](../Topic/IDiaSymbol::get_hasAlloca.md)|`BOOL`|`TRUE` если функция использует выбранную функцию, то памяти \(только SDK для доступа к интерфейсу отладки V8.0 uinnder или более поздней версии\).|  
|[IDiaSymbol::get\_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|`BOOL`|`TRUE` если функция содержит обработку ошибок, C\+\+\-style \(только из пакета SDK для доступа к интерфейсу отладки V8.0 или более поздней версии\).|  
|[IDiaSymbol::get\_hasEHa](../Topic/IDiaSymbol::get_hasEHa.md)|`BOOL`|`TRUE` если функция содержит асинхронную обработку исключений \(только в пакет SDK для доступа к интерфейсу отладки V8.0 или более поздней версии\).|  
|[IDiaSymbol::get\_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|`BOOL`|`TRUE` если функция содержит встроенную сборки \(только из пакета SDK для доступа к интерфейсу отладки V8.0 или более поздней версии\).|  
|[IDiaSymbol::get\_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|`BOOL`|`TRUE` если функция содержит a  [longjmp](/visual-cpp/c-runtime-library/reference/longjmp) вызов \(только из пакета SDK для доступа к интерфейсу отладки V8.0 или более поздней версии\).|  
|[IDiaSymbol::get\_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` если функция содержит проверок безопасности \(только в пакет SDK для доступа к интерфейсу отладки V8.0 или более поздней версии\).|  
|[IDiaSymbol::get\_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|`BOOL`|`TRUE` если функция содержит обработку исключений, состоящую из Win32\-style \(только из пакета SDK для доступа к интерфейсу отладки V8.0 или более поздней версии\).|  
|[IDiaSymbol::get\_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|`BOOL`|`TRUE` если функция содержит a  [setjmp](/visual-cpp/c-runtime-library/reference/setjmp) вызов \(только из пакета SDK для доступа к интерфейсу отладки V8.0 или более поздней версии\).|  
|[IDiaSymbol::get\_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` если функция имеет вернуться из обработки прерываний \(только в пакет SDK для доступа к интерфейсу отладки V8.0 или более поздней версии\).|  
|[IDiaSymbol::get\_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|`TRUE` если функция виртуальный вступления.|  
|[IDiaSymbol::get\_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|`BOOL`|`TRUE` если функция была помечена с одним из  [inline, \_\_inline, \_\_forceinline](../../misc/inline-inline-forceinline.md) атрибуты.|  
|[IDiaSymbol::get\_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|`BOOL`|`TRUE` если функция отмечена  [naked](/visual-cpp/cpp/naked-cpp) атрибут \(только из пакета SDK для доступа к интерфейсу отладки V8.0 или более поздней версии\).|  
|[IDiaSymbol::get\_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE` если функция является статическим \(только в пакет SDK для доступа к интерфейсу отладки V8.0 или более поздней версии\).|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Число байтов кода функции, начиная с расположением.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Символ включающего compiland.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Идентификатор словарного родительского символов.|  
|[IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md)|`DWORD`|Функции могут быть статическими или расположение метаданных. дополнительные сведения см. в разделе [Местоположения символов](../../debugger/debug-interface-access/symbol-locations.md).|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|Имя функции.|  
|[IDiaSymbol::get\_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` если функция не является встроенной функции \(только SDK для доступа к интерфейсу отладки V8.0 n или более поздней версии\).|  
|[IDiaSymbol::get\_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` если функция не доступен \(только в пакет SDK для доступа к интерфейсу отладки V8.0 или более поздней версии\).|  
|[IDiaSymbol::get\_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` если функция не возвращает значение \(только в пакет SDK для доступа к интерфейсу отладки V8.0 или более поздней версии\).|  
|[IDiaSymbol::get\_noStackOrdering](../Topic/IDiaSymbol::get_noStackOrdering.md)|`BOOL`|`TRUE` если функция была компилированна с проверками безопасности буфера, но без упорядочения стека может быть выполнено.|  
|[IDiaSymbol::get\_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` если код содержит сведения для отладки оптимизированного кода \(только в пакет SDK для доступа к интерфейсу отладки V8.0 или более поздней версии\).|  
|[IDiaSymbol::get\_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|`TRUE` если функция чисто виртуальный.|  
|[IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Относительное положение этой функции в качестве модуля.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Идентификатор индекса символа.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Возвращает `SymTagFunction` \(одно из  [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) значения\).|  
|[IDiaSymbol::get\_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|Маркер метаданных для функции.|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Символ для функции сигнатуры.|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Идентификатор типа символа.|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` если функция бесподстроечна.|  
|[IDiaSymbol::get\_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|`BSTR`|Упрощенного форма имени функции \(только из пакета SDK для доступа к интерфейсу отладки v8.0 или более поздние версии\)|  
|[IDiaSymbol::get\_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`BSTR`|Часть или всю упрощенного форма имени функции \(только из пакета SDK для доступа к интерфейсу отладки v8.0 или более поздней версии\).|  
|[IDiaSymbol::get\_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE` если виртуальная функция.|  
|[IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Позиция данной функции внутри исполняемого образа.|  
|[IDiaSymbol::get\_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|Если виртуальная функция, затем смещение в таблице виртуальных функций.|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` если функция помечена как volatile.|  
  
## См. также  
 [Перечисление CV\_access\_e](../../debugger/debug-interface-access/cv-access-e.md)   
 [Лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md)   
 [Местоположения символов](../../debugger/debug-interface-access/symbol-locations.md)