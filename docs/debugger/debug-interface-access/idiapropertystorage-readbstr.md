---
title: IDiaPropertyStorage::ReadBSTR | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBSTR
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f0bff81499fe8ea66ce5d4f50616adfec44d3002
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56610961"
---
# <a name="idiapropertystoragereadbstr"></a>IDiaPropertyStorage::ReadBSTR
Считывает `BSTR` значения в наборе свойств.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT ReadBSTR ( 
   PROPID id,
   BSTR*  pValue
);
```

#### <a name="parameters"></a>Параметры
 `id`

[in] Идентификатор свойства для чтения (`PROPID` определяется в файле WTypes.h как `ULONG`).

 `pValue`

[out] Возвращает значение свойства.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `E_INVALIDARG` Если свойство не имеет типа `BSTR`.

## <a name="remarks"></a>Примечания
 Объект `BSTR` определяется Windows как строку расширенных символов с завершающим нулевым символом.

## <a name="see-also"></a>См. также раздел
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)