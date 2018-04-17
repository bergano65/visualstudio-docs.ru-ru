---
title: MemoryTypeEnum | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 92eaaa63f276d9107dfa3155eb85d52884d3157c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
Указывает тип для доступа к памяти.  
  
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
 Обращается к данным или стек памяти.  
  
 `MemTypeStack`  
 Доступ только стек памяти.  
  
 `MemTypeAny`  
 Обращается к памяти любого типа.  
  
## <a name="remarks"></a>Примечания  
 Значения этого перечисления передаются [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) способ ограничить доступ к различным типам памяти.  
  
## <a name="requirements"></a>Требования  
 Заголовок: cvconst.h  
  
## <a name="see-also"></a>См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)