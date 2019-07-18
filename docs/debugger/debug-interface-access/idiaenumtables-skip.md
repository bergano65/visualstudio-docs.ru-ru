---
title: IDiaEnumTables::Skip | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Skip method
ms.assetid: 5c9db956-0654-4f1a-8775-530aa980d8ec
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24232878452082dd1769c9bc9f1cd22d081968f2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832694"
---
# <a name="idiaenumtablesskip"></a>IDiaEnumTables::Skip
Пропускает указанное число таблиц в последовательности перечисления.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Параметры
 `celt`

[in] Количество таблиц в последовательности перечисления для пропуска.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` Если отсутствуют дополнительные таблицы, чтобы пропустить.

## <a name="see-also"></a>См. также
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)