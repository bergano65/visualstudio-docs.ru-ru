---
title: 'IDiaSymbol:: get_isAcceleratorGroupSharedLocal | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 17a20542-5b45-478f-bb80-0d56031aadb5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d6cf755121f851e652cce251ace2105e6773822
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740336"
---
# <a name="idiasymbolget_isacceleratorgroupsharedlocal"></a>IDiaSymbol::get_isAcceleratorGroupSharedLocal
Получает флаг, указывающий, соответствует ли символ общей локальной переменной группы в коде, скомпилированном для ускорителя C++ amp.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_isAcceleratorGroupSharedLocal(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Параметры
 `pFlag`

заполняет Указатель на `BOOL`, указывающий, соответствует ли символ общей локальной переменной группы в коде, скомпилированном для ускорителя C++ amp. Если `TRUE`, можно использовать методы `get_baseDataSlot` и `get_baseDataOffset`, чтобы получить сведения о местоположении хранилища для переменной.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)
- [IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)