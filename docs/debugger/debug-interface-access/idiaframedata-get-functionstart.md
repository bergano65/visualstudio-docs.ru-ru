---
title: IDiaFrameData::get_functionStart | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_functionStart method
ms.assetid: 49fd24fb-65c2-4812-8303-56a968353e1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43c825bd621ada3f3e81d76f09a1f4bf9e30a67e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839983"
---
# <a name="idiaframedatagetfunctionstart"></a>IDiaFrameData::get_functionStart
Получает флаг, указывающий, содержит ли блок точку входа функции.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_functionStart ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает `TRUE` Если блок содержит точку входа; в противном случае возвращает `FALSE`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 Это возможно для кадра стека, не будут включены начала функции, так как кадр представляет встроенный метод или функция, вставить в функцию.

## <a name="see-also"></a>См. также
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)