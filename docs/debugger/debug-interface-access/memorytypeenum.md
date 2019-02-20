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
ms.openlocfilehash: 6e0f0973c0491cd65c2d03be785bb03b8c2f31df
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227424"
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
`MemTypeCode`  
Доступ только кода памяти.

`MemTypeData`  
Доступ к данных или стек памяти.

`MemTypeStack`  
Доступ только стека памяти.

`MemTypeAny`  
Обращается к памяти любого типа.

## <a name="remarks"></a>Примечания
Значения в этом перечислении передаются [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) способ ограничить доступ к различным типам памяти.

## <a name="requirements"></a>Требования
Заголовок: cvconst.h

## <a name="see-also"></a>См. также раздел
[Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)  
[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
