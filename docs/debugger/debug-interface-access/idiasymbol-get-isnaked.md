---
title: IDiaSymbol::get_isNaked | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isNaked method
ms.assetid: b16629dc-8e17-476b-9c7b-58e7277c61ed
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e45306a831c8767b93e3c1baad0171fcfb60ba6b
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "64790146"
---
# <a name="idiasymbolgetisnaked"></a>IDiaSymbol::get_isNaked
Получает флаг, указывающий, имеет ли функция [с атрибутом naked](/cpp/cpp/naked-cpp) атрибут (то есть функция имеет без кода пролога и эпилога, компилятор добавляет).

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_isNaked(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Параметры
 `pFlag`

[out] Возвращает `TRUE` Если функция имеет `naked` атрибут; в противном случае возвращает `FALSE`.

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
- [Вызовы функций с атрибутом naked](/cpp/cpp/naked-function-calls)