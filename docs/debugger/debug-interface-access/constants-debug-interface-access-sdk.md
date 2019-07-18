---
title: Константы (SDK для доступа к интерфейсу отладки) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed505499efcabd7173fea9d668cd9afa5ed6d925
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62555082"
---
# <a name="constants-debug-interface-access-sdk"></a>Константы (SDK для доступа к интерфейсу отладки)
Эти строковые константы можно использовать для идентификации различные разделы файла базы данных (PDB) программы отладки через пакет SDK для доступа к интерфейсу отладки.

## <a name="constants"></a>Константы
Следующие объявляются как макросы C/C++.

|Макрос|Значение|
|-----------|-----------|
|`DiaTable_Symbols`|L «Символы»|
|`DiaTable_Sections`|L «Разделы»|
|`DiaTable_SrcFiles`|L «SourceFiles»|
|`DiaTable_LineNums`|L «LineNumbers»|
|`DiaTable_SegMap`|L «SegmentMap»|
|`DiaTable_Dbg`|L «Dbg»|
|`DiaTable_InjSrc`|L «InjectedSource»|
|`DiaTable_FrameData`|L «FrameData»|

## <a name="example"></a>Пример
Ниже приведен пример, с помощью одного из следующих символов:

```C++
HRESULT GetSymbolTable(IDiaEnumTables *pEnumTables, IDiaTable **pTable)
{
    HRESULT hr;
    VARIANT var;
    var.vt      = VT_BSTR;
    var.bstrVal = SysAllocString( DiaTable_Symbols );
    hr = pEnumTables->Item( var, pTable );
    return(hr);
}
```

## <a name="requirements"></a>Требования
Заголовок: dia2.h

## <a name="see-also"></a>См. также
- [Ссылки](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)
- [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
