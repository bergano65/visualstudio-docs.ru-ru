---
title: Преобразователь | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- thunk properties [DIA SDK]
- thunk symbol
ms.assetid: 01abb95f-d89a-465c-a4eb-8e8509598c95
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 68e5542f3257ead72c13d454affbd0713325a7b4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62576373"
---
# <a name="thunk"></a>Thunk
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Каждый `thunk` определяется `SymTagThunk` тега.  
  
## <a name="properties"></a>Свойства  
 Ниже приведены свойства, которые являются допустимыми для данного типа символов.  
  
|Свойство|Тип данных|Описание|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Атрибут модификатор доступа, один из [перечисление CV_access_e](../../debugger/debug-interface-access/cv-access-e.md) значения (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Часть смещения расположения; Дополнительные сведения см. в разделе [перечисление LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSegment::get_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|`DWORD`|Раздел частью расположение; Дополнительные сведения см. в разделе [перечисление LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Если какие-либо (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии), включающего родительского класса.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Идентификатор включающего родительского класса символов (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|Значение TRUE, если преобразователь помечается как константа (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|  
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|Значение TRUE, если преобразователь — введение виртуальная функция (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии)|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|Значение TRUE, если преобразователь считается статическим (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Число байтов кода в преобразователь.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Символ для включающего единице компиляции, блок или функции.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Идентификатор лексической родительского символа.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Конечные точки имеют статического расположения; Дополнительные сведения см. в разделе [расположения символов](../../debugger/debug-interface-access/symbol-locations.md) перечисления.|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Имя преобразователя.|  
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|Значение TRUE, если преобразователь чисто виртуально (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Относительное положение этого преобразователя, его модуля.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Идентификатор индекса символа.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Возвращает `SymTagThunk` (один из [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) значения).|  
|[IDiaSymbol::get_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|`DWORD`|Часть смещения местоположения преобразователя целевого объекта.|  
|[IDiaSymbol::get_targetRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress.md)|`DWORD`|Относительный виртуальный адрес преобразователь целевого объекта в качестве включающего блока.|  
|[IDiaSymbol::get_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|`DWORD`|Часть преобразовать конечный раздел.|  
|[IDiaSymbol::get_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|`ULONGLONG`|Целью преобразователь в исполняемом образе.|  
|[IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|`DWORD`|Преобразовать тип в соответствии с определением [перечисление THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md).|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Тип этого преобразователя (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Идентификатор типа символа (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` Если преобразователь не согласована (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии),|  
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE` Если преобразователь является виртуальным (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Положение этого преобразователя в исполняемом образе.|  
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|Смещение в виртуальной таблице этот преобразователь (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` Если преобразователь помечается как volatile (только в версии 8.0 пакет SDK для доступа к интерфейсу отладки или более поздней версии).|  
  
## <a name="see-also"></a>См. также  
 [Лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md)   
 [Перечисление THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md)
