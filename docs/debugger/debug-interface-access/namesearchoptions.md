---
title: Намесеарчоптионс | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NameSearchOptions enumeration
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61905c0c6c40d893cc8723b711d67690133a7155
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738617"
---
# <a name="namesearchoptions"></a>NameSearchOptions
Задает параметры поиска для символов и имен файлов.

## <a name="syntax"></a>Синтаксис

```C++
enum NameSearchOptions {
    nsNone,
    nsfCaseSensitive     = 0x1,
    nsfCaseInsensitive   = 0x2,
    nsfFNameExt          = 0x4,
    nsfRegularExpression = 0x8,
    nsfUndecoratedName   = 0x10,

// For backward compatibility:
    nsCaseSensitive           = nsfCaseSensitive,
    nsCaseInsensitive         = nsfCaseInsensitive,
    nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,
    nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,
    nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive
};
```

## <a name="elements"></a>Элементы
`nsNone` Параметры не указаны.

`nsfCaseSensitive` применяет совпадение имен с учетом регистра.

`nsfCaseInsensitive` применяет совпадение имен без учета регистра.

`nsfFNameExt` обрабатывает имена как пути и применяет имя filename. ext.

`nsfRegularExpression` применяет совпадение имен с учетом регистра, используя звездочки (*) и вопросительные знаки (?) в качестве подстановочных знаков. (Другие распространенные символы регулярных выражений не поддерживаются.)

`nsfUndecoratedName` применяется только к символам, имеющим недекорированные и декорированные имена.

## <a name="remarks"></a>Заметки
Значения из этого перечисления передаются следующим методам:

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>Требования
Заголовок: dia2. h

## <a name="see-also"></a>См. также
- [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
