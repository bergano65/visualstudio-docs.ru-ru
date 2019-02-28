---
title: IDiaEnumTables::get_Count | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::get_Count method
ms.assetid: 30fa316b-a746-4028-acae-4efcd2066f38
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e5cc51a166c5ac70c2db5358b893e52e2242d53
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56629759"
---
# <a name="idiaenumtablesgetcount"></a>IDiaEnumTables::get_Count
Возвращает число таблиц.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_Count (    LONG* pRetVal
);

```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает количество таблиц.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)