---
title: Меморитипинум | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ded136da4d601fd7c11a10c21aac0c90864bc0bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158132"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Указывает тип памяти для доступа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum MemoryTypeEnum {  
   MemTypeCode,  
   MemTypeData,  
   MemTypeStack,  
   MemTypeAny = -1  
};  
```  
  
#### <a name="parameters"></a>Параметры  
 `MemTypeCode`  
 Обращается только к памяти кода.  
  
 `MemTypeData`  
 Обращается к данным или стековой памяти.  
  
 `MemTypeStack`  
 Обращается только к памяти стека.  
  
 `MemTypeAny`  
 Обращается к любому типу памяти.  
  
## <a name="remarks"></a>Remarks  
 Значения в этом перечислении передаются методу [идиастакквалкхелпер:: readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) , чтобы ограничить доступ к различным типам памяти.  
  
## <a name="requirements"></a>Требования  
 Заголовок: квконст. h  
  
## <a name="see-also"></a>См. также:  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
