---
title: IDiaEnumFrameData::frameByRVA | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByRVA method
ms.assetid: 4b8dec05-e76c-4cc4-9644-2369d583849f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbdb525034016981c1f9030e6bce1f9590c45591
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838328"
---
# <a name="idiaenumframedataframebyrva"></a>IDiaEnumFrameData::frameByRVA
Возвращает кадр, относительный виртуальный адрес (RVA).

## <a name="syntax"></a>Синтаксис

```C++
HRESULT frameByRVA( 
   DWORD           relativeVirtualAddress,
   IDiaFrameData** frame
);
```

#### <a name="parameters"></a>Параметры
 relativeVirtualAddress

[in] Относительный виртуальный адрес фрейма интерес.

 фрейм

[out] Возвращает [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) объект, представляющий рамку, содержащую указанный адрес.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если нет кадров данных, соответствующей указанному адресу. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)