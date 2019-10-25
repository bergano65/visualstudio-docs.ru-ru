---
title: 'IDiaEnumTables:: get_Count | Документация Майкрософт'
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
ms.openlocfilehash: e2a03072d2987275144d0e89b678e5282b077f0e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743773"
---
# <a name="idiaenumtablesget_count"></a>IDiaEnumTables::get_Count
Извлекает количество таблиц.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_Count (    LONG* pRetVal
);

```

#### <a name="parameters"></a>Параметры
 `pRetVal`

заполняет Возвращает число таблиц.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)