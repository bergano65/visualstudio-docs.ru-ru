---
title: FuncDebugStart | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- FuncDebugStart symbol
- debugging [DIA SDK], start point
ms.assetid: 1cbc6ca5-87d0-4c30-a39e-0a9dc62ce1a9
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dfd751f6a0d562b2f1b036669d3e7013554a115b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738075"
---
# <a name="funcdebugstart"></a>FuncDebugStart
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Если функция имеет определенные точки, в какие отладки — чтобы начать работу, что точка определена по символу с `SymTagFuncDebugStart` тега.  
  
## <a name="properties"></a>Свойства  
 Ниже приведены свойства, которые являются допустимыми для данного типа символов.  
  
|Свойство.|Тип данных|Описание:|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Часть смещения расположения; Дополнительные сведения см. в разделе [перечисление LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Раздел частью расположение; Дополнительные сведения см. в разделе [перечисление LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` Если эта функция использует пользовательское соглашение об именовании (только в пакет SDK для версии 8.0 или более поздней версии).|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` Если функция выполняет гораздо возвращаемого значения (только в пакет SDK для версии 8.0 или более поздней версии).|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` Если функция содержит отклик на прерывание (только в пакет SDK для версии 8.0 или более поздней версии).|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE` Если функция отмечена как статический (только в пакет SDK для версии 8.0 или более поздней версии).|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Символ для внешней функции.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Идентификатор лексической родительского символа.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Точки начала имеют статический расположений; Дополнительные сведения см. в разделе [расположения символов](../../debugger/debug-interface-access/symbol-locations.md).|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` Если были указаны функции [noinline](http://msdn.microsoft.com/library/f259d55b-dec7-4bde-8cf9-14521e4fdc42) атрибут (только в пакет SDK для версии 8.0 или более поздней версии).|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` Если были указаны функции [noreturn](http://msdn.microsoft.com/library/9c6517e5-22d7-4051-9974-3d2200ae4d1d) атрибут (только в пакет SDK для версии 8.0 или более поздней версии).|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` Если функция никогда не вызывается (только в пакет SDK для версии 8.0 или более поздней версии).|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Смещение символа в памяти; Дополнительные сведения см. в разделе [перечисление LocationType](../../debugger/debug-interface-access/locationtype.md), `LocIsRegRel`.|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` Если код содержит сведения об отладке для оптимизированного кода (только в пакет SDK для версии 8.0 или более поздней версии).|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Относительное положение функции в качестве блока.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Идентификатор индекса символа.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Возвращает `SymTagFuncDebugStart` (один из [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) значения).|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Позиция функции внутри исполняемого файла.|  
  
## <a name="see-also"></a>См. также  
 [Лексическая иерархия символьных типов](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType-перечисление](../../debugger/debug-interface-access/locationtype.md)   
 [Местоположения символов](../../debugger/debug-interface-access/symbol-locations.md)



