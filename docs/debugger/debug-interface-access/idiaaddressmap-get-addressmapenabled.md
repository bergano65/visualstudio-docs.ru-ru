---
title: IDiaAddressMap::get_addressMapEnabled | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7391010e409cc25a3151bb2abb806289c81288a1
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56641890"
---
# <a name="idiaaddressmapgetaddressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
Указывает, установлен ли уже адрес карту для конкретного сеанса.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_addressMapEnabled ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 pRetVal

[out] Возвращает `TRUE` Если включено сопоставление адресов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Исполняемый файл после процессоров иногда обновить исполняемый файл. Доступа к интерфейсу отладки содержит механизм для поддержки преобразования символов для нового макета.

 Клиентские приложения можно задать адрес карты для конкретного сеанса, получая [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md) интерфейс из [IDiaSession](../../debugger/debug-interface-access/idiasession.md) интерфейс и вызвав [IDiaAddressMap::set_ addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) метод, а затем с помощью вызова [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) метод. `get_addressMapEnabled` Метод возвращает результат вызова метода `put_addressMapEnabled` метод.

## <a name="see-also"></a>См. также раздел
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)