---
title: 'IDiaStackFrame:: get_rawLVarInstanceValue | Документация Майкрософт'
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
ms.openlocfilehash: 0b1118517988f6a790cd4f6732eba3bc8a9fc25a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741636"
---
# <a name="idiastackframeget_rawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
Этот метод получает значение указанной локальной переменной в виде необработанных байтов.

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

окне Объект `IDiaLVarInstance`, представляющий экземпляр локальной переменной, для которой нужно получить значение.

 `cbDataMax`

окне Максимальное число байтов в буфере, на которое указывает `pbData`. Это может быть не более 8 байт (`sizeof(ULONGLONG)`).

 `pcbData`

заполняет Возвращает фактическое число байтов, хранящихся в буфере.

 `pbData`

заполняет Буфер для заполнения данными. Не может иметь значение `NULL`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)