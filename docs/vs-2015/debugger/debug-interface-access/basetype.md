---
title: Тип BaseType | Документация Майкрософт
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
- BaseType symbol [DIA SDK]
ms.assetid: 2f9e22e6-8360-496a-ac6b-17a5a56b0c46
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 08606b1d794ab61ebad0293613a6bdc9a4694c18
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771199"
---
# <a name="basetype"></a>BaseType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Базовые типы определяются по `SymTagBaseType` символы.  
  
## <a name="properties"></a>Свойства  
 Ниже приведены дополнительные допустимые свойства для данного типа символов.  
  
|Свойство.|Тип данных|Описание:|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|`DWORD`|Одно из значений из [перечисление BasicType](../../debugger/debug-interface-access/basictype.md).|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` Если базовый тип помечен как const.|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`LONGLONG`|Размер в байтах, базового типа.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Символ, включающего [единице компиляции](../../debugger/debug-interface-access/compiland.md).|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Идентификатор лексической родительского символа.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Идентификатор индекса символа.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Возвращает `SymTagBaseType` (один из [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) значения).|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` Если базовый тип не выровнен.|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` Если базовый тип помечен как переменное.|  
  
## <a name="see-also"></a>См. также  
 [Перечисление BasicType](../../debugger/debug-interface-access/basictype.md)   
 [Иерархия классов символьных типов](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)



