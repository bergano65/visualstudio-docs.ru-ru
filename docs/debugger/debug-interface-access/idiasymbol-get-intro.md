---
title: 'IDiaSymbol:: get_intro | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_intro method
ms.assetid: 101afe4a-4c57-45de-87b4-330394c6de10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4680af2d41ef3fa06a89784003c98982a09c2b63
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740350"
---
# <a name="idiasymbolget_intro"></a>IDiaSymbol::get_intro
Получает флаг, указывающий, представляет ли функция виртуальную функцию.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_intro ( 
    BOOL* pRetVal
);
```

#### <a name="parameters"></a>Параметры
`pRetVal`

заполняет Возвращает `TRUE`, если функция является вводным виртуальным; в противном случае возвращает `FALSE`.

## <a name="return-value"></a>Возвращаемое значение
В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="example"></a>Пример

```C++
class A {
    virtual int f1();
}
class B : public A {
    int f1();
}
```

И `A::f1`, и `B::f1` являются виртуальными функциями, но `A::f1` — это введение виртуальной.

## <a name="requirements"></a>Требования

|Требование|Описание|
|-----------------|-----------------|
|Заголовок:|dia2. h|
|Версия:|Пакет SDK для DIA версии 7.0|

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
