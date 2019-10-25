---
title: 'IDiaEnumTables:: Next | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Next method
ms.assetid: 8d7bd359-d33e-4317-9674-d89283efd7de
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 688652fe3915e1974d5d0e1d04fb1ac075863d8c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743743"
---
# <a name="idiaenumtablesnext"></a>IDiaEnumTables::Next
Извлекает указанное число таблиц в последовательности перечисления.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT Next ( 
   ULONG       celt,
   IDiaTable** rgelt,
   ULONG*      pceltFetched
);
```

#### <a name="parameters"></a>Параметры
 `celt`

окне Число извлекаемых таблиц в перечислителе.

 `rgelt`

заполняет Массив, который должен быть заполнен объектами [идиатабле](../../debugger/debug-interface-access/idiatable.md) , представляющими нужные таблицы.

 `pceltFetched`

заполняет Возвращает количество таблиц в выбранном перечислителе.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE`, если больше нет таблиц. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)