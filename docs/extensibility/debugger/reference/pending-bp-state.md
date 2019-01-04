---
title: PENDING_BP_STATE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- PENDING_BP_STATE
helpviewer_keywords:
- PENDING_BP_STATE enumeration
ms.assetid: ac04ad72-fa92-4a15-ade2-0d0bbbadfc7f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 85b0a686dee156710584263b1bde76b0ae1552a8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53831502"
---
# <a name="pendingbpstate"></a>PENDING_BP_STATE
Указывает состояние ожидающая точка останова (точку останова, которая еще не привязаны).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_PENDING_BP_STATE {   
   PBPS_NONE     = 0x0000,  
   PBPS_DELETED  = 0x0001,  
   PBPS_DISABLED = 0x0002,  
   PBPS_ENABLED  = 0x0003  
};  
typedef DWORD PENDING_BP_STATE;  
```  
  
```csharp  
public enum enum_PENDING_BP_STATE {   
   PBPS_NONE     = 0x0000,  
   PBPS_DELETED  = 0x0001,  
   PBPS_DISABLED = 0x0002,  
   PBPS_ENABLED  = 0x0003  
};  
```  
  
## <a name="members"></a>Участники  
 PBPS_NONE  
 Заполнитель для нуля. Это значение никогда не возвращается.  
  
 PBPS_DELETED  
 Указывает, что ожидающая точка останова была удалена.  
  
 PBPS_DISABLED  
 Указывает, ожидающая точка останова была отключена.  
  
 PBPS_ENABLED  
 Указывает, что ожидающая точка останова включена.  
  
## <a name="remarks"></a>Примечания  
 Использовать в качестве `state` членом [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) структуры.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)