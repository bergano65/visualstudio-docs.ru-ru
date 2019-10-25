---
title: 'IDiaSymbol:: get_hasSecurityChecks | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSecurityChecks method
ms.assetid: 4bb51f62-8645-41a4-bc44-1451010623fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11fd7f70da9ae47b9858f8265d0608e3d6994ef7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740458"
---
# <a name="idiasymbolget_hassecuritychecks"></a>IDiaSymbol::get_hasSecurityChecks
Получает флаг, указывающий, была ли компилируемого объекта или функция скомпилирована с помощью проверки безопасности переполнения буфера (например, параметр компилятора [/GS (проверка безопасности буфера)](/cpp/build/reference/gs-buffer-security-check) ).

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_hasSecurityChecks(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Параметры
 `pFlag`

заполняет Возвращает `TRUE`, если функция имеет какие – либо проверки безопасности; в противном случае возвращает `FALSE`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="requirements"></a>Требования

|Требование|Описание|
|-----------------|-----------------|
|Заголовок:|dia2. h|
|Версия:|Пакет SDK для DIA v 8.0|

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [/GS (проверка безопасности буфера)](/cpp/build/reference/gs-buffer-security-check)