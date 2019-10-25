---
title: 'IDiaStackFrame:: get_registerValue | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_registerValue method
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d270b9b177367c9a15c2b64f6f8bc5607c5a459d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741626"
---
# <a name="idiastackframeget_registervalue"></a>IDiaStackFrame::get_registerValue
Получает значение указанного регистра, хранящееся в кадре стека.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_registerValue(
   ULONG      registerIndex,
   ULONGLONG *pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `registerIndex`

окне Одно из значений перечисления [перечисления CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) .

 `pRetVal`

заполняет Значение, хранящееся в регистре.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [Перечисление CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)