---
title: 'IDiaSymbol:: Финдчилдрен | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildren method
ms.assetid: 5fe7573a-e48b-428d-9c17-7421b7209246
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f3c62271f6324e50a68de393cfa668c69ba4a935
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741290"
---
# <a name="idiasymbolfindchildren"></a>IDiaSymbol::findChildren
Возвращает дочерние элементы символа.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT findChildren ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Параметры
 `symtag`

окне Задает Теги символов для извлекаемых дочерних элементов, как определено в [перечислении симтаженум](../../debugger/debug-interface-access/symtagenum.md). Задайте значение `SymTagNull`, чтобы получить все дочерние элементы.

 `name`

окне Указывает имя извлекаемых дочерних элементов. Задайте значение `NULL`, чтобы получить все дочерние элементы.

 `compareFlags`

окне Задает параметры сравнения, применяемые к соответствию имен. Значения из перечисления [перечисления намесеарчоптионс](../../debugger/debug-interface-access/namesearchoptions.md) можно использовать отдельно или в сочетании.

 `ppResult`

заполняет Возвращает объект [идиаенумсимболс](../../debugger/debug-interface-access/idiaenumsymbols.md) , содержащий список извлеченных дочерних символов.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает `S_OK`, если хотя бы один дочерний элемент символа был найден, или `S_FALSE` значение, если не найдено потомков. в противном случае возвращает код ошибки.

## <a name="remarks"></a>Заметки
 Этот метод идентичен вызову метода [IDiaSession:: финдчилдрен](../../debugger/debug-interface-access/idiasession-findchildren.md) с этим символом в качестве первого параметра.

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [Перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)