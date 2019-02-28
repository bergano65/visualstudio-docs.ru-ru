---
title: Функция (доступа к интерфейсу отладки пакета SDK) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Function symbol
ms.assetid: 458dc91c-b78b-4427-84f4-615d89e26760
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d1e0af87618955c492bef68be45c8c623f41218
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56634049"
---
# <a name="function-debug-interface-access-sdk"></a>Function (SDK для доступа к интерфейсу отладки)
Каждая функция, определяемая параметром `SymTagFunction` символов.

## <a name="properties"></a>Свойства
 Ниже приведены свойства, которые являются допустимыми для данного типа символов.

|Свойство.|`Data type`|Описание|
|--------------|-----------------|-----------------|
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Одно из значений из [перечисление CV_access_e](../../debugger/debug-interface-access/cv-access-e.md), если функция является функцией-членом.|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Часть смещения расположения; Дополнительные сведения см. в разделе [перечисление LocationType](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Раздел частью расположение; Дополнительные сведения см. в разделе [перечисление LocationType](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Символ для класса, если функция является функцией-членом.|
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Идентификатор символа родительского класса.|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` Если функция отмечена как константа.|
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` Если эта функция использует пользовательское соглашение об именовании (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` Если функция выполняет гораздо возвращаемого значения (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|
|[IDiaSymbol::get_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|`BOOL`|`TRUE` Если функция используется функция выделенной памяти (только uinnder V8.0 пакета SDK для доступа к интерфейсу отладки или более поздней версии).|
|[IDiaSymbol::get_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|`BOOL`|`TRUE` Если функция содержит стиле C++, обрабатывающего (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|
|[IDiaSymbol::get_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|`BOOL`|`TRUE` Если функция содержит асинхронное исключение обработки (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|
|[IDiaSymbol::get_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|`BOOL`|`TRUE` Если функция содержит встроенной сборке (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|
|[IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|`BOOL`|`TRUE` Если функция содержит [longjmp](/cpp/c-runtime-library/reference/longjmp) вызова (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` Если функция содержит проверок безопасности (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|
|[IDiaSymbol::get_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|`BOOL`|`TRUE` Если функция содержит структурированные стиле Win32, обрабатывающего (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|
|[IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|`BOOL`|`TRUE` Если функция содержит [setjmp](/cpp/c-runtime-library/reference/setjmp) вызова (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` Если функция возвращает из прерывания (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|`TRUE` Если функция является введение виртуальных.|
|[IDiaSymbol::get_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|`BOOL`|`TRUE` Если функция помечена с помощью одного из [встроенные, __inline, \__forceinline](/cpp/cpp/inline-functions-cpp) атрибуты.|
|[IDiaSymbol::get_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|`BOOL`|`TRUE` Если функция помечена атрибутом [с атрибутом naked](/cpp/cpp/naked-cpp) атрибут (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE` Если функция является статическим (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Число байтов кода функции, начиная с позиции.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Символ включающего единице компиляции.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Идентификатор лексической родительского символа.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Функции могут иметь статический метод или метаданных расположений; Дополнительные сведения см. в разделе [расположения символов](../../debugger/debug-interface-access/symbol-locations.md).|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Имя функции.|
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` Если функция не является встроенной функцией (только n DIA SDK версии 8.0 или более поздней версии).|
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` Если функцию не удается добиться (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` Если функция не возвращает значение (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|
|[IDiaSymbol::get_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|`BOOL`|`TRUE` Если функция был скомпилирован с помощью проверки безопасности буфера, но не порядок стека можно сделать.|
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` Если код содержит сведения об отладке для оптимизированного кода (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|`TRUE` Если функция является чисто виртуальной.|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Относительное положение этой функции в пределах его модуля.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Идентификатор индекса символа.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Возвращает `SymTagFunction` (один из [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) значения).|
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|Токен метаданных для функции.|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Символ для сигнатуры функции.|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Идентификатор типа символа.|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` Если функция не выровнен.|
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|`BSTR`|Недекорированной форме имени функции (только в пакет SDK для версии 8.0 или более поздней версии)|
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`BSTR`|Частично или полностью недекорированной форме имени функции (только в пакет SDK для версии 8.0 или более поздней версии).|
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE` Если виртуальная функция.|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Позиция для данной функции в исполняемом образе.|
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|Если виртуальная функция, затем смещение в таблице виртуальных функций.|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` Если функция отмечена как переменное.|

## <a name="see-also"></a>См. также раздел
- [Перечисление CV_access_e](../../debugger/debug-interface-access/cv-access-e.md)
- [Лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md)
- [Местоположения символов](../../debugger/debug-interface-access/symbol-locations.md)