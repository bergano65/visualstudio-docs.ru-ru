---
title: 'IDiaSymbol:: get_isLTCG | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isLTCG method
ms.assetid: 5f7f05b8-6b71-4958-9e1e-e4924ef9c59b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d3fa97d5612b61151d9c435b91f500c87af0b23
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740218"
---
# <a name="idiasymbolget_isltcg"></a>IDiaSymbol::get_isLTCG
Получает флаг, указывающий, был ли [компилируемого объекта](../../debugger/debug-interface-access/compiland.md) связан с параметром компоновщика [/LTCG (создание кода во время компоновки)](/cpp/build/reference/ltcg-link-time-code-generation), который помогает в оптимизации всей программы. Этот параметр применяется только к управляемому коду.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_iSLTCG(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Параметры
 пфлаг

заполняет Возвращает `TRUE`, если `compiland` был связан с параметром компоновщика/LTCG; в противном случае возвращает `FALSE`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="requirements"></a>Требования

|Требование|Описание|
|-----------------|-----------------|
|Заголовок:|dia2. h|
|Версия:|Пакет SDK для DIA v 8.0|

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)