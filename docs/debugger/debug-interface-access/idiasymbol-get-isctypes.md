---
title: 'IDiaSymbol:: get_isCTypes | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2 interface
ms.assetid: 00c73cf9-2933-472e-bc1d-d041f4d7e412
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64be123de60608aa82e2e271b1f14d0de7be2cb4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740279"
---
# <a name="idiasymbolget_isctypes"></a>IDiaSymbol::get_isCTypes
Получает флаг, указывающий, содержит ли файл символов типы C.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_isCTypes(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Параметры
 `pFlag`

заполняет Возвращает `TRUE`, если файл символов содержит типы C; в противном случае возвращает `FALSE`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="remarks"></a>Заметки
 Это свойство доступно из `SymTagExe` типа символов (см. [exe](../../debugger/debug-interface-access/exe.md)).

## <a name="requirements"></a>Требования

|Требование|Описание|
|-----------------|-----------------|
|Заголовок:|dia2. h|
|Версия:|Пакет SDK для DIA v 8.0|

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Exe](../../debugger/debug-interface-access/exe.md)