---
title: 'IDiaSession:: Финдинлинилинесбирва | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 7a74d5ee-0dbf-47c0-92b4-47ec03b13ce9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6cf587d9e369ac32c72df5e1fd7a9005ef417177
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742210"
---
# <a name="idiasessionfindinlineelinesbyrva"></a>IDiaSession::findInlineeLinesByRVA
Извлекает перечисление, позволяющее клиенту выполнять итерацию по сведениям о номере строки всех функций, которые прямо или косвенно связаны с указанным родительским символом и содержатся в указанном относительном виртуальном адресе (RVA).

## <a name="syntax"></a>Синтаксис

```C++
HRESULT findInlineeLinesByRVA ( 
   IDiaSymbol*           parent,
   DWORD                 rva,
   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Параметры
 `parent`

окне Объект `IDiaSymbol`, представляющий родительский элемент.

 `rva`

окне Указывает адрес в виде RVA.

 `length`

окне Указывает диапазон адресов (в байтах), который охватывает этот запрос.

 `ppResult`

заполняет Содержит объект `IDiaEnumLineNumbers`, содержащий список извлекаемых номеров строк.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)