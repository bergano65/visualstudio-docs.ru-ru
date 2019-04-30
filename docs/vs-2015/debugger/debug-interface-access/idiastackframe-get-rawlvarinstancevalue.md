---
title: IDiaStackFrame::get_rawLVarInstanceValue | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8ff78c38ad077084b3dea9c96e3251ffddb2206
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62573018"
---
# <a name="idiastackframegetrawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
Этот метод получает значение указанной локальной переменной в виде необработанных байт.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_rawLVarInstanceValue(
   IDiaLVarInstance* pInstance,
   DWORD             cbDataMax,
   DWORD*            pcbData,
   BYTE*             pbData
);
```

#### <a name="parameters"></a>Параметры
 `pInstance`

[in] `IDiaLVarInstance` Объект, представляющий экземпляр локальной переменной, чтобы получить значение.

 `cbDataMax`

[in] Максимальное число байтов в буфере, на которые указывают `pbData`. Это может быть более 8 байт (`sizeof(ULONGLONG)`).

 `pcbData`

[out] Возвращает фактическое число байтов, сохраненных в буфере.

 `pbData`

[out] Буфер для заполниться данными. Не может иметь значение `NULL`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)