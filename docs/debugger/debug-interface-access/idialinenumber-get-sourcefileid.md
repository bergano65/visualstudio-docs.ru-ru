---
title: IDiaLineNumber::get_sourceFileId | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_sourceFileId method
ms.assetid: 4f482a1e-e85f-4173-98de-8e5f7622554b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be0fffc1c52c6e15e4ac564cb3e53c60a3670c22
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56610688"
---
# <a name="idialinenumbergetsourcefileid"></a>IDiaLineNumber::get_sourceFileId
Извлекает уникальный исходный файл идентификатор для исходного файла, который участвует в этой строке.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_sourceFileId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает идентификатор файла уникальный источника для исходного файла, который участвует в этой строке.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)