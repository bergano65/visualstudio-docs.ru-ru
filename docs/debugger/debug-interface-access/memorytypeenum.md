---
title: MemoryTypeEnum | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 4a8dcf657933cf62f3f2173bb89dadd1366b0cec
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822947"
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
  
## <a name="see-also"></a>См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)