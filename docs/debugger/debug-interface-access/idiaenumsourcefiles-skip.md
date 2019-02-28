---
title: IDiaEnumSourceFiles::Skip | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Skip method
ms.assetid: 4821e6dd-d33f-403d-857d-e3ae81e4a9e3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b80a2a0f270ccd76d052d4c7863170448648e138
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56597469"
---
# <a name="idiaenumsourcefilesskip"></a>IDiaEnumSourceFiles::Skip
Пропускает указанное число исходных файлов в последовательности перечисления.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Параметры
 celt

[in] Количество исходных файлов в последовательности перечисления для пропуска.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` Если нет другие исходные файлы, чтобы пропустить.

## <a name="see-also"></a>См. также раздел
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)