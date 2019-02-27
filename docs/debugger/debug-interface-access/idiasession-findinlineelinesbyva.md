---
title: IDiaSession::findInlineeLinesByVA | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: dffe6594-e0d1-4ed5-aeea-8773f88d82a6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 58f572fcce0b490fad8f94f1e3e3d941e8568211
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56642915"
---
# <a name="idiasessionfindinlineelinesbyva"></a>IDiaSession::findInlineeLinesByVA
Возвращает перечисление, которое позволяет клиенту для выполнения итерации по информация о номере строки всех функций, которые являются встроенными, напрямую или косвенно, символ из указанного родительского объекта и содержащихся в указанный виртуальный адрес (VA).

## <a name="syntax"></a>Синтаксис

```C++
HRESULT findInlineeLinesByVA ( 
   IDiaSymbol*           parent,   ULONGLONG             va,   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Параметры
 `parent`

[in] `IDiaSymbol` Объект, представляющий родительский объект.

 `va`

[in] Указывает адрес как ва.

 `length`

[in] Указывает диапазон адресов, в байтах, чтобы охватить с этим запросом.

 `ppResult`

[out] Содержит `IDiaEnumLineNumbers` , содержащий список номеров строк, возвращаемых.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)