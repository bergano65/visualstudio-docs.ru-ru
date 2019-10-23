---
title: 'IDiaSymbol:: get_addressOffset | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressOffset method
ms.assetid: c15639b0-7f37-46c7-891b-40273b7f6319
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9290173fc9dcfdc07c7c0afbb33c741fe3e53f6c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741090"
---
# <a name="idiasymbolget_addressoffset"></a>IDiaSymbol::get_addressOffset
Извлекает смещение части адреса. Используйте, если для [перечисления локатионтипе](../../debugger/debug-interface-access/locationtype.md) задано значение `LocIsStatic`.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_addressOffset ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

заполняет Возвращает часть смещения адреса.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="remarks"></a>Заметки
 Для статических элементов, расположенных во внешней библиотеке DLL, смещение, возвращаемое этим методом, может быть равно 0, так как этот метод полагается на получение виртуального адреса члена. Виртуальные адреса допустимы только в том случае, если метод [IDiaSession::P ut_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) в интерфейсе [IDiaSession](../../debugger/debug-interface-access/idiasession.md) был вызван с ненулевым параметром, ЗАДАЮЩИМ адрес загрузки библиотеки DLL.

 Чтобы получить часть адреса раздела, вызовите метод [IDiaSymbol:: get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md) .

## <a name="requirements"></a>Требования

|Требование|Описание|
|-----------------|-----------------|
|Заголовок:|dia2. h|
|Версия:|Пакет SDK для DIA версии 7.0|

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md)
- [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)
- [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)