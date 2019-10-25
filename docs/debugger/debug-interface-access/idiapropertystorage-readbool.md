---
title: 'Идиапропертистораже:: Реадбул | Документация Майкрософт'
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
ms.openlocfilehash: d776e37bab189e61d0264f4cbda24f89cb4501ce
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742928"
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
Считывает `BOOL` значений в наборе свойств.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT ReadBOOL ( 
   PROPID id,
   BOOL*  pValue
);
```

#### <a name="parameters"></a>Параметры
 `id`

окне Идентификатор считываемого свойства (`PROPID` определен в Втипес. h как `ULONG`).

 `pValue`

заполняет Возвращает значение свойства.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `E_INVALIDARG`, если свойство не имеет тип `BOOL`.

## <a name="remarks"></a>Заметки
 Для обеспечения единообразия результатов следует интерпретировать `BOOL` значение, чтобы ненулевые значения `TRUE` и нулевые `FALSE`.

## <a name="see-also"></a>См. также
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)