---
title: IDiaFrameData::get_lengthSavedRegisters | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthSavedRegisters method
ms.assetid: dfda4e91-9bfa-4b9d-9133-b73015bfa4d5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4e05ebb4d7a58be353bb933a4ce5e5053d8dbf33
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56599925"
---
# <a name="idiaframedatagetlengthsavedregisters"></a>IDiaFrameData::get_lengthSavedRegisters
Возвращает число байтов, сохраненных регистров в стек.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_lengthSavedRegisters ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает число байтов, сохраненных регистров.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 Значение, возвращаемое этим методом обычно используется в интерпретации строки программы (см. в разделе [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) метод для определения строки программы).

## <a name="see-also"></a>См. также раздел
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)