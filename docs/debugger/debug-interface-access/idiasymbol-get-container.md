---
title: 'IDiaSymbol:: get_container | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_container method
ms.assetid: 24e832eb-80b3-484c-a41b-11477ec9de99
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0533eb2cdea1dd3e1bea3d64e2b94ce29a09353d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740780"
---
# <a name="idiasymbolget_container"></a>IDiaSymbol::get_container
Эта функция получает указатель на символ, представляющий родительский объект или контейнер этого символа.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_container(
   IDiaSymbol **pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

заполняет Возвращает указатель на `IDiaSymbol`, содержащий сведения о контейнере этого символа.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает значение S_OK; в противном случае возвращает S_FALSE или код ошибки.

> [!NOTE]
> Возвращаемое значение S_FALSE означает, что свойство недоступно для символа.

## <a name="requirements"></a>Требования

|Требование|Описание|
|-----------------|-----------------|
|Заголовок:|dia2. h|
|Версия:|Пакет SDK для DIA v 8.0|

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)