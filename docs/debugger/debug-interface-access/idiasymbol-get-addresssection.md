---
title: 'IDiaSymbol:: get_addressSection | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressSection method
ms.assetid: fe80d479-3bb5-4f55-9b62-1bd58d0a60ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a468fe6ee8a8d7d00bb2e6c261d50919a1dd764
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741079"
---
# <a name="idiasymbolget_addresssection"></a>IDiaSymbol::get_addressSection
Извлекает часть расположения адреса. Используйте, если для [перечисления локатионтипе](../../debugger/debug-interface-access/locationtype.md) задано значение `LocIsStatic`.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_addressSection ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

заполняет Возвращает часть расположения адреса.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="remarks"></a>Заметки
 Для статических элементов, расположенных во внешней библиотеке DLL, раздел, возвращаемый этим методом, может иметь значение 0, так как этот метод полагается на получение виртуального адреса члена. Виртуальные адреса допустимы только в том случае, если метод [IDiaSession::P ut_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) в интерфейсе [IDiaSession](../../debugger/debug-interface-access/idiasession.md) был вызван с ненулевым параметром, ЗАДАЮЩИМ адрес загрузки библиотеки DLL.

 Чтобы получить смещение части адреса, вызовите метод [IDiaSymbol:: get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md) .

## <a name="requirements"></a>Требования

|Требование|Описание|
|-----------------|-----------------|
|Заголовок:|dia2. h|
|Версия:|Пакет SDK для DIA версии 7.0|

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md)