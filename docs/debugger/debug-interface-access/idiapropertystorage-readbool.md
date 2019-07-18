---
title: IDiaPropertyStorage::ReadBOOL | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5cc189283d6e9910b0b01d3d3e1ca28165bf500
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839697"
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
Считывает `BOOL` значения в наборе свойств.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT ReadBOOL ( 
   PROPID id,
   BOOL*  pValue
);
```

#### <a name="parameters"></a>Параметры
 `id`

[in] Идентификатор свойства для чтения (`PROPID` определяется в файле WTypes.h как `ULONG`).

 `pValue`

[out] Возвращает значение свойства.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `E_INVALIDARG` Если свойство не имеет типа `BOOL`.

## <a name="remarks"></a>Примечания
 Согласованные результаты интерпретировать `BOOL` значение таким образом, ненулевыми значениями `TRUE` а нулевое — `FALSE`.

## <a name="see-also"></a>См. также
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)