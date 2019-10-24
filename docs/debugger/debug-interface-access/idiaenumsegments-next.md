---
title: 'Идиаенумсегментс:: Next | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Next method
ms.assetid: 53f61874-d821-47ab-a1f5-27e982804a6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34062b654cbaccec053c5ac50bfb041d37a0f4e6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744190"
---
# <a name="idiaenumsegmentsnext"></a>IDiaEnumSegments::Next
Извлекает указанное количество сегментов в последовательности перечисления.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT Next ( 
   ULONG         celt,
   IDiaSegment** rgelt,
   ULONG*        pceltFetched
);
```

#### <a name="parameters"></a>Параметры
 celt

окне Число извлекаемых сегментов в перечислителе.

 rgelt

заполняет Массив, который должен быть заполнен требуемыми объектами [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) , представляющими сегменты.

 pceltFetched

заполняет Возвращает количество сегментов в полученном перечислителе.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE`, если больше нет сегментов. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)