---
title: IDiaSymbol::get_offsetInUdt | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_offsetInUdt method
ms.assetid: 442f20d9-9d6a-44a1-83fb-c3f8c14b6c97
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 19e99f48f344ad96b35251aadf86e3787c809ca7
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611949"
---
# <a name="idiasymbolgetoffsetinudt"></a>IDiaSymbol::get_offsetInUdt
Получает смещение в начале определяемого пользователем типа (UDT) члена в определяемый пользователем тип.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_offsetInUdt( 
   DWORD* pRetVal)
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает смещение в байтах расположения символов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="remarks"></a>Примечания
 Эта функция используется только в локальном записей при оптимизированном построении.

## <a name="requirements"></a>Требования
 Заголовок: Dia2.h

 Библиотека: diaguids.lib

 DLL: msdia100.dll

## <a name="see-also"></a>См. также раздел
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)