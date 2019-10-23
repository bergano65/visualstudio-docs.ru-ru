---
title: 'Идиаинжектедсаурце:: get_sourceCompression | Документация Майкрософт'
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
ms.openlocfilehash: 9428b30df82d92a8c74511644aaf97f2166807a2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743321"
---
# <a name="idiainjectedsourceget_sourcecompression"></a>IDiaInjectedSource::get_sourceCompression
Возвращает индикатор используемого сжатия источника.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_sourceCompression ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

заполняет Возвращает индикатор используемого сжатия источника. Нулевое значение указывает, что сжатие источника не использовалось.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE`, если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Заметки
 Значение, возвращаемое этим методом, зависит от используемого компилятора. Например, компилятор может использовать кодирование длины выполнения или сжатие в стиле Хаффмана.

## <a name="see-also"></a>См. также
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)