---
title: IDiaSymbol::get_noStackOrdering | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_noStackOrdering method
ms.assetid: a1753917-705b-4165-9880-d05e91e6dcb4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0774477ac200ca7c810cf4a7e5925c137b292c85
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633399"
---
# <a name="idiasymbolgetnostackordering"></a>IDiaSymbol::get_noStackOrdering
Эта функция получает флаг, указывающий, можно ли сделать нет упорядоченности стека как часть проверки буфера стека ([/GS (проверка безопасности буфера)](/cpp/build/reference/gs-buffer-security-check) параметр компилятора).

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_noStackOrdering(
   BOOL *pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает `TRUE` если упорядочение не стека можно сделать как часть проверки для буфера стека; в противном случае возвращает `FALSE`.

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
- [/GS (проверка безопасности буфера)](/cpp/build/reference/gs-buffer-security-check)