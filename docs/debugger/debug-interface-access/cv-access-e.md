---
title: CV_access_e | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bbe338ba9d3aa6cbc795606c3fa285526afdfd36
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745358"
---
# <a name="cv_access_e"></a>CV_access_e
Задает область видимости (уровень доступа) функций и переменных-членов.

## <a name="syntax"></a>Синтаксис

```C++
typedef enum CV_access_e {
    CV_private   = 1,
    CV_protected = 2,
    CV_public    = 3
} CV_access_e;
```

## <a name="elements"></a>Элементы
У члена CV_private есть закрытый доступ.

Член CV_protected имеет защищенный доступ.

Член CV_public имеет открытый доступ.

## <a name="remarks"></a>Заметки
Спецификатор доступа `friend` не указан здесь, так как обычно используется функциями, не являющимися членами, которые имеют доступ как к частным, так и к защищенным элементам класса. Используйте метод [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) для поиска символов с доступом к `SymTagFriend`.

## <a name="requirements"></a>Требования
Заголовок: квконст. h

## <a name="see-also"></a>См. также
- [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
