---
title: IDiaSymbol::get_intro | Документация Майкрософт
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
ms.openlocfilehash: 020d631405586227d91fd06fb1794ab5554d1075
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/13/2019
ms.locfileid: "56226914"
---
# <a name="idiasymbolgetintro"></a>IDiaSymbol::get_intro
Получает флаг, указывающий, является ли функция Знакомство с виртуальной функцией.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_intro ( 
    BOOL* pRetVal
);
```

#### <a name="parameters"></a>Параметры
`pRetVal`  
[out] Возвращает `TRUE` Если функция является введение виртуальным; в противном случае возвращает `FALSE`.

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

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

Оба `A::f1` и `B::f1` — это виртуальные функции, но `A::f1` является введение виртуальным.

## <a name="requirements"></a>Требования

|Требование|Описание|
|-----------------|-----------------|
|Заголовок:|dia2.h|
|Версия:|ПАКЕТ SDK для версии 7.0|

## <a name="see-also"></a>См. также раздел
[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
