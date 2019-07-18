---
title: Измерение | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Dimension Symbol
ms.assetid: 94f791da-bfea-454f-8a14-da31e8e1596a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97b03f1a3ceb8424cc3e533512f6d0d3e034f791
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554809"
---
# <a name="dimension"></a>Измерение
Каждый массив FORTRAN имеет измерения, который определяется параметром `SymTagDimension` символов.

## <a name="properties"></a>Свойства
 Ниже приведены дополнительные допустимые свойства для данного типа символов.

|Свойство|Тип данных|Описание|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_lowerBound](../../debugger/debug-interface-access/idiasymbol-get-lowerbound.md)|`IDiaSymbol*`|Нижняя граница массива измерения FORTRAN.|
|[IDiaSymbol::get_lowerBoundId](../../debugger/debug-interface-access/idiasymbol-get-lowerboundid.md)|`DWORD`|Идентификатор символа, нижняя граница.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Идентификатор индекса символа.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Возвращает `SymTagDimension` (один из [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) значения).|
|[IDiaSymbol::get_upperBound](../../debugger/debug-interface-access/idiasymbol-get-upperbound.md)|`IDiaSymbol*`|Верхняя граница FORTRAN измерения массива.|
|[IDiaSymbol::get_upperBoundId](../../debugger/debug-interface-access/idiasymbol-get-upperboundid.md)|`DWORD`|Идентификатор верхней границы символа.|

## <a name="see-also"></a>См. также
- [ArrayType](../../debugger/debug-interface-access/arraytype.md)
- [Иерархия классов символьных типов](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)