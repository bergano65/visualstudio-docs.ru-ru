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
ms.openlocfilehash: b10ab87f056bc153ec41c125b0e01ddefa139b80
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745402"
---
# <a name="constants-debug-interface-access-sdk"></a>Константы (SDK для доступа к интерфейсу отладки)
Эти строковые константы можно использовать для обнаружения различных разделов файла базы данных отладки (PDB) с помощью пакета SDK DIA.

## <a name="constants"></a>Константы
Следующие объявления объявляются как C/C++ макросы.

|Макрос|значения|
|-----------|-----------|
|`DiaTable_Symbols`|L "символы"|
|`DiaTable_Sections`|L "разделы"|
|`DiaTable_SrcFiles`|L "SourceFiles"|
|`DiaTable_LineNums`|L "Линенумберс"|
|`DiaTable_SegMap`|L "Сегментмап"|
|`DiaTable_Dbg`|L "DBG"|
|`DiaTable_InjSrc`|L "Инжектедсаурце"|
|`DiaTable_FrameData`|L "Фрамедата"|

## <a name="example"></a>Пример
Ниже приведен пример использования одного из следующих символов:

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
Заголовок: dia2. h

## <a name="see-also"></a>См. также
- [Ссылка](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)
- [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
