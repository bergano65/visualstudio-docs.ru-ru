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
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596351"
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

## <a name="see-also"></a>См. также раздел
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)