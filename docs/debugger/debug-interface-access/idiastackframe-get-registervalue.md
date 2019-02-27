---
title: IDiaStackFrame::get_registerValue | Документация Майкрософт
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
ms.openlocfilehash: a819293863b658f6e12609b2c1cd83c37532e02d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56637637"
---
# <a name="idiastackframegetregistervalue"></a>IDiaStackFrame::get_registerValue
Возвращает значение указанного регистра, как хранящиеся в кадре стека.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_registerValue(
   ULONG      registerIndex,
   ULONGLONG *pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `registerIndex`

[in] Один из [перечисление CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) значений перечисления.

 `pRetVal`

[out] Значение, хранящееся в регистре.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [Перечисление CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)