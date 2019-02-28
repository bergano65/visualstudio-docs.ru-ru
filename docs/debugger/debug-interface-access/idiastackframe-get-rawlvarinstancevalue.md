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
ms.openlocfilehash: a8ad236307360a96f64999313764424305980fc9
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56624026"
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

## <a name="see-also"></a>См. также раздел
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)