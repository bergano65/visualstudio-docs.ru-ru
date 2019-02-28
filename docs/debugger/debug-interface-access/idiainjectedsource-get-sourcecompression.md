---
title: IDiaInjectedSource::get_sourceCompression | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_sourceCompression method
ms.assetid: 854b142f-23a9-466c-bf7f-98e581d5abcd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00c7783752a183e8afc580c4c74285add8a51041
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56629798"
---
# <a name="idiainjectedsourcegetsourcecompression"></a>IDiaInjectedSource::get_sourceCompression
Получает индикатор того, источник сжатия, используемый.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_sourceCompression ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает индикатор, источник сжатия, используемый. Нулевое значение указывает, что было использовано без сжатия источника.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 Значение, возвращаемое этим методом зависит от используемого компилятора. Предположим, например компилятор использует сжатие длин кодирования или стиле Хаффмана.

## <a name="see-also"></a>См. также раздел
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)