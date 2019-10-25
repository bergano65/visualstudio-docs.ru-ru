---
title: IDiaAddressMap::p ut_addressMapEnabled | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5fe5589b667054ee75e3b01743553a2d60bef92
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745064"
---
# <a name="idiaaddressmapput_addressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
Указывает, следует ли использовать карту адресов для преобразования адресов символов.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT put_addressMapEnabled ( 
   BOOL NewVal
);
```

#### <a name="parameters"></a>Параметры
 неввал

окне Задайте значение `TRUE`, чтобы включить перевод символов, или `FALSE` для отключения.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Заметки
 Исполняемые процедуры, выполняемые после выполнения обработчиков, иногда обновляют исполняемый файл. DIA содержит механизм для поддержки перевода символов в новый макет.

 При загрузке PDB-файла таблица адресов, хранимая в файле, становится доступной. Однако бывают случаи, когда клиентскому приложению может потребоваться предоставить собственную карту адресов, вызвав метод [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) . Если метод `set_addressMap` успешно выполнен, клиентское приложение должно вызвать метод `put_addressMapEnabled` с параметром `NewVal` `TRUE`, чтобы разрешить использование этой гиперкарты адресов.

 Текущее состояние включенной таблицы адресов можно получить с помощью вызова метода [IDiaAddressMap:: get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) .

## <a name="see-also"></a>См. также
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)