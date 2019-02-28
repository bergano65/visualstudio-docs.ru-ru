---
title: IDiaPropertyStorage::ReadLONG | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadLONG
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2fb277368e23cf51a4d3d3b69226ee6bf093d6c3
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56615576"
---
# <a name="idiapropertystoragereadlong"></a>IDiaPropertyStorage::ReadLONG
Считывает `LONG` значения в наборе свойств.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT ReadDLONG ( 
   PROPID id,
   LONG*  pValue
);
```

#### <a name="parameters"></a>Параметры
 `id`

[in] Идентификатор свойства для чтения (`PROPID` определяется в файле WTypes.h как `ULONG`).

 `pValue`

[out] Возвращает значение свойства.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `E_INVALIDARG` Если свойство не имеет типа `LONG`.

## <a name="remarks"></a>Примечания
 Объект `LONG` определяется Windows как 32-разрядное целое число со знаком.

## <a name="see-also"></a>См. также раздел
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)