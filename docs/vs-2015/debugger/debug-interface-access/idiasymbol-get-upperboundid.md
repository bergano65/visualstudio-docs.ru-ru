---
title: IDiaSymbol::get_upperBoundId | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_upperBoundId method
ms.assetid: ddfa1617-bd0f-4187-ba77-a225bab93a95
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2cca35fb1369214672b8740d41f65a2a725517e3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63385868"
---
# <a name="idiasymbolgetupperboundid"></a>IDiaSymbol::get_upperBoundId
Извлекает идентификатор символа верхнюю границу измерения массива FORTRAN.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_upperBoundId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`
- [out] Возвращает идентификатор символ, представляющий верхнюю границу измерения массива FORTRAN.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="remarks"></a>Примечания
 Идентификатор — это уникальное значение, созданные с помощью пакета SDK доступа к интерфейсу отладки, чтобы пометить все символы как уникальный.

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)