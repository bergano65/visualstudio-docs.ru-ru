---
title: IDiaSymbol::get_optimizedCodeDebugInfo | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_optimizedCodeDebugInfo method
ms.assetid: 57ef4170-37a9-46b0-8217-c1a674725113
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7058b24ec04f3d69f1e8a4e8a497962948091f15
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56647115"
---
# <a name="idiasymbolgetoptimizedcodedebuginfo"></a>IDiaSymbol::get_optimizedCodeDebugInfo
Получает флаг, указывающий, содержит ли функция отладочной информации, характерное для оптимизированного кода.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_optimizedCodeDebugInfo(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Параметры
 `pFlag`

[out] Возвращает `TRUE` Если Оптимизированная функция или метка содержит сведения об отладке; в противном случае возвращает `FALSE`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="requirements"></a>Требования

|Требование|Описание|
|-----------------|-----------------|
|Заголовок:|dia2.h|

## <a name="see-also"></a>См. также раздел
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)