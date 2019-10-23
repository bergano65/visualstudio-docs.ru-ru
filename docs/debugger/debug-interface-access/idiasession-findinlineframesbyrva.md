---
title: 'IDiaSession:: Финдинлинефрамесбирва | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ddb3ff0e-cb3d-4fa0-af56-f064b218b264
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 329bf9f4fa94171347eeea8fc9f2744b7ce4269f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742157"
---
# <a name="idiasessionfindinlineframesbyrva"></a>IDiaSession::findInlineFramesByRVA
Извлекает перечисление, позволяющее клиенту выполнять итерацию всех встроенных кадров на указанном относительном виртуальном адресе (RVA).

## <a name="syntax"></a>Синтаксис

```C++
HRESULT findInlineFramesByRVA ( 
   IDiaSymbol*       parent,   DWORD             rva,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Параметры
 `parent`

окне Объект `IDiaSymbol`, представляющий родительский элемент.

 `rva`

окне Указывает адрес в виде RVA.

 `ppResult`

заполняет Содержит объект `IDiaEnumSymbols`, содержащий список извлекаемых кадров.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)