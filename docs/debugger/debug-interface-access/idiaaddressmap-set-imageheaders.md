---
title: 'IDiaAddressMap:: set_imageHeaders | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef17e1073c67ede75d075b18773129c287349c0d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745016"
---
# <a name="idiaaddressmapset_imageheaders"></a>IDiaAddressMap::set_imageHeaders
Задает заголовки изображений для включения преобразования относительных виртуальных адресов.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT set_imageHeaders ( 
   DWORD cbData,
   BYTE  data[],
   BOOL  originalHeaders
);
```

#### <a name="parameters"></a>Параметры
 cbData

окне Число байтов данных заголовка. Должен быть `n*sizeof(IMAGE_SECTION_HEADER)`, где `n` — число заголовков разделов в исполняемом файле.

 data[]

окне Массив структур `IMAGE_SECTION_HEADER`, которые будут использоваться в качестве заголовков изображений.

 оригиналхеадерс

окне Задайте значение `FALSE`, если заголовки изображений относятся к новому образу, `TRUE`, если они соответствуют исходному изображению до обновления. Как правило, это значение будет `TRUE` только в сочетании с вызовами метода [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Заметки
 Структура `IMAGE_SECTION_HEADER` объявляется в Winnt. h и представляет формат заголовка раздела Image исполняемого файла.

 Относительные вычисления виртуальных адресов зависят от значений `IMAGE_SECTION_HEADER`. Обычно DIA извлекает эти данные из файла базы данных программы (. pdb). Если эти значения отсутствуют, DIA не может вычислить относительные виртуальные адреса, а метод [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) возвращает `FALSE`. Затем клиент должен вызвать метод [IDiaAddressMap::P ut_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) , чтобы включить вычисление относительного виртуального адреса после предоставления отсутствующих заголовков изображений из самого образа.

## <a name="see-also"></a>См. также
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)