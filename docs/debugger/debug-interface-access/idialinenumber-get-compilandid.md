---
title: IDiaLineNumber::get_compilandId | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_compilandId method
ms.assetid: 2cd6f551-8091-47c7-803f-3f79a766a211
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9874dec57c873164ec1875f31fd15c817781bb7a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839931"
---
# <a name="idialinenumbergetcompilandid"></a>IDiaLineNumber::get_compilandId
Извлекает уникальный идентификатор для компилируемого объекта, который участвует в этой строке.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_compilandId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает `DWORD` , содержащее уникальный идентификатор для компилируемого объекта, который участвует в этой строке.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)