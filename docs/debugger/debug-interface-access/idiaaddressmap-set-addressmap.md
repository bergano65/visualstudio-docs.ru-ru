---
title: 'IDiaAddressMap:: set_addressMap | Документация Майкрософт'
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
ms.openlocfilehash: 8414788af44d78943088b78b2d3e42a5a8d8c50b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745028"
---
# <a name="idiaaddressmapset_addressmap"></a>IDiaAddressMap::set_addressMap
Предоставляет карту адресов для поддержки перевода макета изображения.

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

окне Число элементов в параметре `data`.

 `data[]`

окне Массив структур [структуры диааддрессмапентри](../../debugger/debug-interface-access/diaaddressmapentry.md) , определяющий карту трансляции.

 `imagetoSymbols`

[in] `TRUE`, если параметр `data` определяет карту из нового макета изображения в исходный макет (как описано в отладочных символах). `FALSE`, если `data` является картой для нового макета изображения, полученного из исходного макета.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Заметки
 Обычно DIA извлекает карты преобразования адресов из файла базы данных программы (. pdb). Если эти значения отсутствуют, метод [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) вызывается дважды, один раз, если для параметра `imagetoSymbols` установлено значение `TRUE` и один раз с параметром `imagetoSymbols`, для которого задано значение `FALSE`. Переводы сопоставления адресов нельзя включить с помощью метода [IDiaAddressMap::P ut_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) , если не указаны оба сопоставления перевода.

## <a name="see-also"></a>См. также
- [Структура DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)