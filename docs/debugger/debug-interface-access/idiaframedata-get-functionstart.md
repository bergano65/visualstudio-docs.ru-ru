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
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56614731"
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

## <a name="see-also"></a>См. также раздел
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)