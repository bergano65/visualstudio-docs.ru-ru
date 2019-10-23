---
title: 'IDiaEnumTables:: Item | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf2d6b14f17d42a128e59446e27bfc251de40d17
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743754"
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
Извлекает таблицу с помощью индекса или имени.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT Item ( 
   VARIANT     index,
   IDiaTable** table
);
```

#### <a name="parameters"></a>Параметры
 `index`

окне Индекс или имя извлекаемого объекта [идиатабле](../../debugger/debug-interface-access/idiatable.md) . Если используется целочисленный вариант, он должен находиться в диапазоне от 0 до `count`-1, где `count` возвращается методом [IDiaEnumTables:: get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) .

 `table`

заполняет Возвращает объект [идиатабле](../../debugger/debug-interface-access/idiatable.md) , представляющий нужную таблицу.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Заметки
 Если указан строковый вариант, то строка будет указывать на конкретную таблицу. Имя должно быть одним из имен таблиц, как определено в [константах (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md).

## <a name="example"></a>Пример

```C++
VARIANT var;
var.vt = VT_BSTR;
var.bstrVal = SysAllocString(DiaTable_Symbols );
IDiaTable* pTable;
pEnumTables->Item( var, &pTable );
```

## <a name="see-also"></a>См. также
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)
- [Константы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)