---
title: IDiaStackFrame::get_functionStart | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_functionStart
ms.assetid: e3e6e88b-0594-4d82-9457-480239a2e85a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56a1c700b2a98b51f846e5f1136ef45c67fd5f99
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832080"
---
# <a name="idiastackframegetfunctionstart"></a>IDiaStackFrame::get_functionStart
Получает флаг, указывающий, содержит ли блок точку входа функции.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_functionStart ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает `TRUE` Если кадр стека содержит точку входа функции; в противном случае возвращает `FALSE`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)