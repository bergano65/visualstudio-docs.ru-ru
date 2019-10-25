---
title: 'IDiaAddressMap:: get_addressMapEnabled | Документация Майкрософт'
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
ms.openlocfilehash: b518cf3728279ea8db267d01867fa66ceae35b21
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745183"
---
# <a name="idiaaddressmapget_addressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
Указывает, была ли установлена схема адресов для конкретного сеанса.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_addressMapEnabled ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 претвал

заполняет Возвращает `TRUE`, если сопоставление адресов включено.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Заметки
 Исполняемые процедуры, выполняемые после выполнения обработчиков, иногда обновляют исполняемый файл. DIA содержит механизм для поддержки перевода символов в новый макет.

 Клиентские приложения могут задать карту адресов для конкретного сеанса, получив интерфейс [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md) из интерфейса [IDiaSession](../../debugger/debug-interface-access/idiasession.md) и вызвав метод [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) , а затем выполнив вызов [метода IDiaAddressMap::p метод ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) . Метод `get_addressMapEnabled` возвращает результаты вызова метода `put_addressMapEnabled`.

## <a name="see-also"></a>См. также
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)