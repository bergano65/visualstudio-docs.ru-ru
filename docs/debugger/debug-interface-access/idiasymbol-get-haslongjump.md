---
title: IDiaSymbol::get_hasLongJump | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasLongJump method
ms.assetid: 14484cb1-43b0-47a1-a9a8-081b55566886
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70036cd8add5c9c72262f29ba92fa6c7eaf8977d
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "64817137"
---
# <a name="idiasymbolgethaslongjump"></a>IDiaSymbol::get_hasLongJump
Получает флаг, указывающий, содержит ли функция использование [longjmp](/cpp/c-runtime-library/reference/longjmp) команды (связан с [setjmp](/cpp/c-runtime-library/reference/setjmp) команды, они образуют метод C-стиля обработки исключений).

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_hasLongJump
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Параметры
 `pFlag`

[out] Возвращает `TRUE` Если функция содержит `longjmp` команды; в противном случае возвращает `FALSE`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="requirements"></a>Требования

|Требование|Описание|
|-----------------|-----------------|
|Заголовок:|dia2.h|
|Версия:|ПАКЕТ SDK для версии 8.0|

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)
- [longjmp](/cpp/c-runtime-library/reference/longjmp)
- [setjmp](/cpp/c-runtime-library/reference/setjmp)