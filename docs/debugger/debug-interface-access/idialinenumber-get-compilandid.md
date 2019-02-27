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
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56610919"
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

## <a name="see-also"></a>См. также раздел
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)