---
title: IDiaEnumTables::Next | Документация Майкрософт
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
ms.openlocfilehash: 15a9ebbd3a3993568e4b6496e04661a63290399e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56598758"
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

[in] Количество таблиц в перечислителе требуется получить.

 `rgelt`

[out] Массив, который должен быть заполнен с помощью [IDiaTable](../../debugger/debug-interface-access/idiatable.md) объекты, представляющие нужные таблицы.

 `pceltFetched`

[out] Возвращает количество таблиц в выбранных перечислитель.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если отсутствуют дополнительные таблицы. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)