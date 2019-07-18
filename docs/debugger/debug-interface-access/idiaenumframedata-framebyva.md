---
title: IDiaEnumFrameData::frameByVA | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByVA method
ms.assetid: 0b1e441b-710a-46d8-8060-bed39071c834
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 62999d8b8dc0313e9ca5086dc4737d7a41db1c87
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838224"
---
# <a name="idiaenumframedataframebyva"></a>IDiaEnumFrameData::frameByVA
Возвращает кадр, виртуальный адрес (VA).

## <a name="syntax"></a>Синтаксис

```C++
HRESULT frameByVA( 
   ULONGLONG       virtualAddress,
   IDiaFrameData** frame
);
```

#### <a name="parameters"></a>Параметры
 virtualAddress

[in] VA кадра интерес.

 фрейм

[out] Возвращает [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) , представляющий рамку, содержащую указанный адрес.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если нет кадров данных, соответствующей указанному адресу. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)