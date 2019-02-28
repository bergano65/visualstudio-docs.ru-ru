---
title: IDiaSymbol::get_noReturn | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_noReturn method
ms.assetid: 704c1cc0-5b84-4334-a02a-70f43aff39d5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4cd768220b25ec93ffdb4f038db475304db71333
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56605540"
---
# <a name="idiasymbolgetnoreturn"></a>IDiaSymbol::get_noReturn
Получает флаг, указывающий, был ли функция помечен как никогда не возвращает [noreturn](/cpp/cpp/noreturn) атрибута.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_noReturn(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Параметры
 pFlag

[out] Возвращает `TRUE` Если функция была объявлена как никогда не возвращает `noreturn` атрибут; в противном случае возвращает `FALSE`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="requirements"></a>Требования

|Требование|Описание|
|-----------------|-----------------|
|Заголовок:|dia2.h|
|Версия:|ПАКЕТ SDK для версии 8.0|

## <a name="see-also"></a>См. также раздел
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [noreturn](/cpp/cpp/noreturn)