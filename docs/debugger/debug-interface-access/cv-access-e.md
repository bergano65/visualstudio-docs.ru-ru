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
ms.openlocfilehash: 90230bd95e1dbcd3e4c186257c6c36faad6ba1f7
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56605478"
---
# <a name="cvaccesse"></a>CV_access_e
Задает область видимости (уровень доступа) для функций-членов и переменных.

## <a name="syntax"></a>Синтаксис

```C++
typedef enum CV_access_e {
    CV_private   = 1,
    CV_protected = 2,
    CV_public    = 3
} CV_access_e;
```

## <a name="elements"></a>Элементы
Элемент CV_private имеет закрытый доступ.

Член CV_protected имеет защищенный доступ.

Элемент CV_public имеет общий доступ.

## <a name="remarks"></a>Примечания
`friend` Спецификатор доступа, здесь не так, как они обычно используются не являющиеся членами функции, которые имеют доступ к закрытым и защищенным элементам класса. Используйте [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) поиск символов с помощью метода `SymTagFriend` доступа.

## <a name="requirements"></a>Требования
Заголовок: cvconst.h

## <a name="see-also"></a>См. также раздел
- [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
