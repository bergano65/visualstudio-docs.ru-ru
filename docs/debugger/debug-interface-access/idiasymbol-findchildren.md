---
title: IDiaSymbol::findChildren | Документация Майкрософт
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
ms.openlocfilehash: 5199be7307fdaa607f5aa6a5f554d9fcc82f452d
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "62837827"
---
# <a name="idiasymbolfindchildren"></a>IDiaSymbol::findChildren
Получает дочерние узлы, символа.

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

[in] Задает теги символов требуется получить дочерние элементы, как определено в [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md). Значение `SymTagNull` для всех дочерних элементов, требуется получить.

 `name`

[in] Задает имя используемого дочерние элементы должны быть получены. Значение `NULL` для всех дочерних элементов, требуется получить.

 `compareFlags`

[in] Задает параметры сравнения, который применяется к соответствующим именем. Значения из [перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) перечисления можно использовать отдельно или в сочетании.

 `ppResult`

[out] Возвращает [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) извлечь объект, содержащий список дочерних символов.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает `S_OK` Если по крайней мере одного дочернего элемента этот символ найден, или возвращает `S_FALSE` дочерние элементы не найдены; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод идентичен вызову [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md) метод этот символ в качестве первого параметра.

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [Перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)