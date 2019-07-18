---
title: IDiaSymbol::findInlineFramesByAddr | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 36a122e6-f27e-40cd-9784-cdaf279e1905
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a1a5af94d6a5d6100f8ffb6047f57ee59f780da5
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "62831728"
---
# <a name="idiasymbolfindinlineframesbyaddr"></a>IDiaSymbol::findInlineFramesByAddr
Возвращает перечисление, которое позволяет клиентам выполнять итерацию всех встроенных кадров по указанному адресу.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT findInlineFramesByAddr ( 
   DWORD             isect,
   DWORD             offset,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Параметры
 `isect`

[in] Задает компонент прокрутки на разделе адреса.

 `offset`

[in] Задает компонент прокрутки на смещения адреса.

 `ppResult`

[out] Содержит `IDiaEnumSymbols` , содержащий список кадров, которые извлекаются.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)