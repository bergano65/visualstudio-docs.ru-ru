---
title: IDiaSymbol::get_liveRangeStartAddressSection | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartAddressSection
ms.assetid: 892b80ff-5957-4233-b4d7-6144167be289
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c99b5a14a321a28bdbe7337dcc7cdfa5febdad5d
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "64786526"
---
# <a name="idiasymbolgetliverangestartaddresssection"></a>IDiaSymbol::get_liveRangeStartAddressSection
Возвращает часть раздела начальный адрес диапазона, в котором локальный символ является допустимой.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_liveRangeStartAddressSection ( 
   DWORD* section
);
```

#### <a name="parameters"></a>Параметры
 `section`

[out] Возвращает компонент разделе начальный адрес диапазона.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

> [!NOTE]
> Возвращен код ошибки означает, что символ не имеет сведения о динамической диапазона.

## <a name="remarks"></a>Примечания
 Адрес, образованное раздела и смещение — это начало диапазона, в котором символ является допустимой.

 Чтобы получить смещения часть адреса, используйте [IDiaSymbol::get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md).

## <a name="requirements"></a>Требования
 Заголовок: dia2.h

 Библиотека: diaguids.lib

 DLL: msdia100.dll

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)