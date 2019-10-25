---
title: 'Идиапропертистораже:: Реадулонглонг | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadULONGLONG
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dde2f111e468b8ccf6c1d91440f06d3e7048a0f6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742850"
---
# <a name="idiapropertystoragereadulonglong"></a>IDiaPropertyStorage::ReadULONGLONG
Считывает `ULONGLONG` значений в наборе свойств.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT ReadULONGLONG ( 
   PROPID     id,
   ULONGLONG* pValue
);
```

#### <a name="parameters"></a>Параметры
 `id`

окне Идентификатор считываемого свойства (`PROPID` определен в Втипес. h как `ULONG`).

 `pValue`

заполняет Возвращает значение свойства.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `E_INVALIDARG`, если свойство не имеет тип `ULONGLONG`.

## <a name="remarks"></a>Заметки
 @No__t_0 определяется Windows как 64-разрядное целое число без знака.

## <a name="see-also"></a>См. также
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)