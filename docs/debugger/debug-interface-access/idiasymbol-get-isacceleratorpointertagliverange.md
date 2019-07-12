---
title: IDiaSymbol::get_isAcceleratorPointerTagLiveRange | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d195aec4-6d3c-42e0-88a5-3d463539f0b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8bf20f43fcc8da48a6e1ec1dfd0f65b14f8ad86
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "62836906"
---
# <a name="idiasymbolgetisacceleratorpointertagliverange"></a>IDiaSymbol::get_isAcceleratorPointerTagLiveRange
Получает флаг, указывающий, соответствует ли символ к *символ диапазона определения* для тега компонента переменной указателя в коде, скомпилированном для ускорителя C++ AMP. Символ определения диапазона — расположение переменной для диапазона адресов.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_isAcceleratorPointerTagLiveRange(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Параметры
 `pFlag`

[out] Указатель на `BOOL` , указывающее, соответствует ли символ к символу definition диапазона.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)