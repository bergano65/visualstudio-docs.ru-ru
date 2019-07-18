---
title: IDiaSession::findSymbolByToken | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByToken method
ms.assetid: 3c92149c-6eef-454f-86be-66e89557b9e6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f342efce1c05e305a3e55d6372d1862b04b1197
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62827315"
---
# <a name="idiasessionfindsymbolbytoken"></a>IDiaSession::findSymbolByToken
Получает символ, который содержит заданным токеном метаданных.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT findSymbolByToken ( 
   ULONG        token,
   SymTagEnum   symtag,
   IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>Параметры
 `token`

[in] Указывает токен.

 `symtag`

[in] Найти тип символа. Значения берутся из [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) перечисления.

 `ppSymbol`

[out] Возвращает [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) извлечь объект, представляющий символ.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="example"></a>Пример

```C++
IDiaSymbol* pFunc;
pSession->findSymbolByToken( token, SymTagFunction, &pFunc );
```

## <a name="see-also"></a>См. также
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)