---
title: IDiaSymbol::get_framePointerPresent | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_framePointerPresent method
ms.assetid: d036090a-1651-454d-9130-b798f58ba053
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7914845bccb43ce302665428c824bbf3ebb2c819
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "64825340"
---
# <a name="idiasymbolgetframepointerpresent"></a>IDiaSymbol::get_framePointerPresent
Получает флаг, указывающий, присутствует ли этот указатель фрейма. Используется, когда [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) присваивается `SymTagFunction`.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_framePointerPresent( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out]] Возвращает `TRUE` при наличии; в противном случае этот указатель фрейма возвращает `FALSE`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="remarks"></a>Примечания

## <a name="requirements"></a>Требования
 Заголовок: dia2.h

 Библиотека: diaguids.lib

 DLL: msdia100.dll

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)