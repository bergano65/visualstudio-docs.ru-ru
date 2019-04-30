---
title: IDiaSymbol::get_offset | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_offset method
ms.assetid: 8292bb08-4dc8-4663-beb4-258f5d5a448d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0016ca267b3eaf2535896aab1ee58a470a192c9a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63399452"
---
# <a name="idiasymbolgetoffset"></a>IDiaSymbol::get_offset
Получает смещение расположения символов. Используется, когда [перечисление LocationType](../../debugger/debug-interface-access/locationtype.md) — `LocIsRegRel` или `LocIsBitField`.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_offset ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает смещение в байтах расположения символов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="remarks"></a>Примечания
 Смещение считается от какой-то момент известных обнаружены. Например, смещение `LocIsBitField` расположение типом обычно является от начала содержащего класса.

## <a name="requirements"></a>Требования

|Требование|Описание|
|-----------------|-----------------|
|Заголовок:|dia2.h|
|Версия:|ПАКЕТ SDK для версии 7.0|

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md)