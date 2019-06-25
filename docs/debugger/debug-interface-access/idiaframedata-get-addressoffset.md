---
title: IDiaFrameData::get_addressOffset | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_addressOffset method
ms.assetid: b68e2e68-6483-4936-bf97-1b0a13cb75e2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4460f5102fbb5fd62f332f41a2901d1759731e7f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829099"
---
# <a name="idiaframedatagetaddressoffset"></a>IDiaFrameData::get_addressOffset
Извлекает часть смещения адреса кода для кадра.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_addressOffset ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает часть смещения адреса кода для кадра.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)