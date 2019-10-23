---
title: IDiaAddressMap::p ut_imageAlign | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b1a6bf037dc87d84fab21622571158fb0682f60
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745053"
---
# <a name="idiaaddressmapput_imagealign"></a>IDiaAddressMap::put_imageAlign
Задает выравнивание изображения.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT put_imageAlign ( 
   DWORD NewVal
);
```

#### <a name="parameters"></a>Параметры
 неввал

окне Новое значение выравнивания изображения для исполняемого файла.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Заметки
 Образы (загруженные исполняемые файлы) согласовываются с указанными границами памяти. Это выравнивание может зависеть от текущей системной архитектуры и параметров компиляции и времени компоновки. Выравнивание изображения всегда находится в пределах диапазона байтов. Допустимы следующие значения выравнивания изображения: 1, 2, 4, 8, 16, 32 и 64 байты.

 Текущее выравнивание изображения можно получить с помощью вызова метода [IDiaAddressMap:: get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) .

> [!NOTE]
> Изображение уже загружено в момент, когда этот метод может быть вызван. Метод `put_imageAlign` обычно используется, когда изображение было перемещено или изменено, и требуется новое выравнивание.

## <a name="see-also"></a>См. также
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)