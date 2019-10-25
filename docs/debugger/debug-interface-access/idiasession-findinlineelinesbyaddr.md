---
title: IDiaSession::findInlineeLinesByAddr | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: bb70e408-eed1-4c9c-b5b1-44323125f48b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 496f6b569b3ac02c625ddf18406b78fdb1687be2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742232"
---
# <a name="idiasessionfindinlineelinesbyaddr"></a>IDiaSession::findInlineeLinesByAddr
Извлекает перечисление, позволяющее клиенту выполнять итерацию по сведениям о номере строки всех функций, которые прямо или косвенно связаны с указанным родительским символом и содержатся в указанном диапазоне адресов.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT findInlineeLinesByAddr ( 
   IDiaSymbol*           parent,   DWORD                 isect,   DWORD                 offset,   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Параметры
 `parent`

окне Объект `IDiaSymbol`, представляющий родительский элемент.

 `isect`

окне Указывает компонент раздела адреса.

 `offset`

окне Указывает компонент смещения адреса.

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