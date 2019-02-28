---
title: MemoryTypeEnum | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 19776c8d4ef72149c575d6835e9265e9cdb33727
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56622675"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
Указывает тип доступа к памяти.

## <a name="syntax"></a>Синтаксис

```C++
enum MemoryTypeEnum {
    MemTypeCode,
    MemTypeData,
    MemTypeStack,
    MemTypeAny = -1
};
```

#### <a name="parameters"></a>Параметры
`MemTypeCode` Доступ только кода памяти.

`MemTypeData` Доступ к данных или стек памяти.

`MemTypeStack` Доступ только стека памяти.

`MemTypeAny` Обращается к памяти любого типа.

## <a name="remarks"></a>Примечания
Значения в этом перечислении передаются [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) способ ограничить доступ к различным типам памяти.

## <a name="requirements"></a>Требования
Заголовок: cvconst.h

## <a name="see-also"></a>См. также раздел
- [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
