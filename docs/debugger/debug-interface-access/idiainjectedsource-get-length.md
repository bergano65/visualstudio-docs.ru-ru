---
title: IDiaInjectedSource::get_length | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_length method
ms.assetid: 38b88b8b-c2e0-4b2d-8b8b-9ff373733e78
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8333c7e57c3cd3f240f8a72dd865e458b23bc299
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616031"
---
# <a name="idiainjectedsourcegetlength"></a>IDiaInjectedSource::get_length
Возвращает число байтов кода.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_length ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает число байтов кода.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 Значение, возвращаемое этим методом, длина исходного кода и то же значение, возвращенное [IDiaInjectedSource::get_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md) метод.

## <a name="see-also"></a>См. также раздел
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
- [IDiaInjectedSource::get_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)