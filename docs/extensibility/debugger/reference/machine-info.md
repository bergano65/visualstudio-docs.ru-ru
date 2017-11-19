---
title: "MACHINE_INFO | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MACHINE_INFO
helpviewer_keywords: MACHINE_INFO structure
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3dcaaf72f3279285c8babc64afaecd2f280931dc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="machineinfo"></a>MACHINE_INFO
Описывает конкретного компьютера.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct tagMACHINE_INFO {   
   MACHINE_INFO_FIELDS Fields;  
   BSTR                bstrName;  
   MACHINE_INFO_FLAGS  Flags;  
} MACHINE_INFO;  
```  
  
```csharp  
public struct MACHINE_INFO {   
   public uint   Fields;  
   public string bstrName;  
   public uint   Flags;  
};  
```  
  
## <a name="members"></a>Члены  
 `Fields`  
 Сочетание флагов из [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) перечисления, укажите, какие поля структуры инициализируются.  
  
 `bstrName`  
 Имя компьютера. Аналогичен вызову [GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md).  
  
 `Flags`  
 Сочетание флагов из [MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) перечисление, описывающее атрибуты машины.  
  
## <a name="remarks"></a>Примечания  
 Эта структура возвращается путем вызова [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)   
 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)