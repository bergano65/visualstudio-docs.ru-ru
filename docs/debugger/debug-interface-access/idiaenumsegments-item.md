---
title: 'Идиаенумсегментс:: Item | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Item method
ms.assetid: ee44dd55-39a0-4b7b-97ff-2e1226eeb2bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 101821e3c00d3aeac9b131ee5a11ab9a01e090a9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744184"
---
# <a name="idiaenumsegmentsitem"></a>IDiaEnumSegments::Item
Извлекает сегмент с помощью индекса.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT Item ( 
   DWORD         index,
   IDiaSegment** segment
);
```

#### <a name="parameters"></a>Параметры
 индекс

окне Индекс объекта [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) для извлечения. Индекс находится в диапазоне от 0 до `count`-1, где `count` возвращается методом [идиаенумсегментс:: get_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md) .

 сегмент

заполняет Возвращает объект [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) , представляющий нужный сегмент.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)