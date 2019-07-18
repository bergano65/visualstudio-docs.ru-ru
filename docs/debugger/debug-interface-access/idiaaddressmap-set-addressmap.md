---
title: IDiaAddressMap::set_addressMap | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 963ee64b639780bae60a4c2655db8b666d87c702
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554252"
---
# <a name="idiaaddressmapsetaddressmap"></a>IDiaAddressMap::set_addressMap
Предоставляет адрес сопоставляются поддерживают переводы макет изображения.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT set_addressMap ( 
   DWORD                     cbData,
   struct DiaAddressMapEntry data[],
   BOOL                      imagetoSymbols
);
```

#### <a name="parameters"></a>Параметры
 `cbData`

[in] Число элементов в `data` параметра.

 `data[]`

[in] Массив [структура DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md) структуры, которые определяют схему преобразования.

 `imagetoSymbols`

[in] `TRUE` Если `data` параметр определяет сопоставление из новый макет изображения исходного макета (как определено отладочные символы). `FALSE` Если `data` — это сопоставление новый макет изображения, берутся из исходного макета.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Как правило доступа к интерфейсу отладки извлекает перевода карты из PDB-файла программы. Если эти значения отсутствуют, [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) метод вызывается дважды, один раз с `imagetoSymbols` параметру присвоить `TRUE` и один раз с `imagetoSymbols` параметру присвоить `FALSE`. Преобразования адресов карты нельзя включить, используя [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) метод, если не предоставляются обоих сопоставлениях перевода.

## <a name="see-also"></a>См. также
- [Структура DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)