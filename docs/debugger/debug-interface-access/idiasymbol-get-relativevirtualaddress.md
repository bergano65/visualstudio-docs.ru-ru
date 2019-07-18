---
title: IDiaSymbol::get_relativeVirtualAddress | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_relativeVirtualAddress method
ms.assetid: e37219e3-c021-4057-9ec8-4f7cf3c13a15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bae5deab3a2c7d6d9f912ed584fbdb5961e09612
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "64796359"
---
# <a name="idiasymbolgetrelativevirtualaddress"></a>IDiaSymbol::get_relativeVirtualAddress
Возвращает относительный виртуальный адрес (RVA) расположение. Используется, когда [перечисление LocationType](../../debugger/debug-interface-access/locationtype.md) присваивается `LocIsStatic`.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_relativeVirtualAddress ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает относительный виртуальный адрес расположения.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="example"></a>Пример

```C++
IDiaSymbol* pSymbol;
DWORD       rva;
pSymbol->get_relativeVirtualAddress( &rva );
```

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md)