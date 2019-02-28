---
title: IDiaLineNumber::get_sourceFile | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_sourceFile method
ms.assetid: 86fc4411-375e-4b99-8f96-4da2c3f68190
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e026b837205a8bf62f5d33dc2f5449d40cc485e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619710"
---
# <a name="idialinenumbergetsourcefile"></a>IDiaLineNumber::get_sourceFile
Извлекает ссылку на исходный файл.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_sourceFile ( 
   IDiaSourceFile** pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) объект, представляющий исходный файл.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)