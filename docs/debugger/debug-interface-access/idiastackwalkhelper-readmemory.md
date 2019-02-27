---
title: IDiaStackWalkHelper::readMemory | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 530b6c3f6873724f8a8ca06ea4228b017de281f9
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694469"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
Считывает блок данных из исполняемого файла изображения в памяти.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT readMemory( 
   enum MemoryTypeEnum type,
   ULONGLONG           va,
   DWORD               cbData,
   DWORD*              pcbData,
   BYTE*               pbData
);
```

#### <a name="parameters"></a>Параметры
 `type`

[in] Значение из [перечисление MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) перечисление, определяющее тип памяти для чтения.

 va

[in] Виртуальный адрес в образе, с которого начинается чтение.

 `cbData`

[in] Размер буфера данных в байтах.

 `pcbData`

[out] Возвращает число фактически считанных байтов. Если `pbData` — `NULL`, то это общее число байтов доступных данных.

 `pbData`

[in, out] Буфер, который заполняется память чтения.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [Перечисление MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md)