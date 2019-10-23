---
title: 'Идиаенумфрамедата:: Item | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Item method
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c15f395e7f4aa576c5f69b0f1c61f37ca808fb6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744615"
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
Извлекает элемент данных кадра с помощью индекса.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT Item ( 
   DWORD           index,
   IDiaFrameData** section
);
```

#### <a name="parameters"></a>Параметры
 индекс

окне Индекс объекта [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) для извлечения. Индекс находится в диапазоне от 0 до `count`-1, где `count` возвращается методом [идиаенумфрамедата:: get_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md) .

 section

заполняет Возвращает объект [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) , представляющий нужный элемент данных кадра.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)