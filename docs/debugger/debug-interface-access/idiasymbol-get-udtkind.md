---
title: IDiaSymbol::get_udtKind | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_udtKind method
ms.assetid: 4002f887-aea6-4475-b302-67c57079fe0a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34faf217f77bd30ba707f5ae17886b05dac8ab4f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63401348"
---
# <a name="idiasymbolgetudtkind"></a>IDiaSymbol::get_udtKind
Извлекает все разнообразие определяемого пользователем типа (UDT).

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_udtKind ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает значение из [перечисление UdtKind](../../debugger/debug-interface-access/udtkind.md) перечисление, указывающее тип определяемого пользователем типа: структуры, класса или объединения.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Перечисление UdtKind](../../debugger/debug-interface-access/udtkind.md)