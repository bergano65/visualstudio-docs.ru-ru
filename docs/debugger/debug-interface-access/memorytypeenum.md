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
ms.openlocfilehash: 42cfe138aa6be00628d319f01e7cccfbb4cc4f8a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55040168"
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