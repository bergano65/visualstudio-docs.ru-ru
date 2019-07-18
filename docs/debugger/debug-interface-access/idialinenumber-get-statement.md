---
title: IDiaLineNumber::get_statement | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_statement method
ms.assetid: 22b8ee29-79ef-427f-bd05-00d255ab836b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 397873a65176024327f371e9727b15984cd7d03f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62828387"
---
# <a name="idialinenumbergetstatement"></a>IDiaLineNumber::get_statement
Получает флаг, указывающий, что здесь строки содержатся сведения о начале инструкцию, а не выражение, в исходном коде программы.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_statement ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает `TRUE` Если этой строки описаны в начало оператора в исходном коде программы.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 Операторы могут занимать несколько строк. Этот метод указывает, если номер строки связанной отмечает начало таких многострочного оператора.

## <a name="see-also"></a>См. также
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)