---
title: "PENDING_BP_STATE | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PENDING_BP_STATE
helpviewer_keywords: PENDING_BP_STATE enumeration
ms.assetid: ac04ad72-fa92-4a15-ade2-0d0bbbadfc7f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: de7ac105f7dea0c57297c29a4bdb8d5c85f62321
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="pendingbpstate"></a>PENDING_BP_STATE
Указывает состояние ожидающая точка останова (точка останова, которая еще не привязаны).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_PENDING_BP_STATE {   
   PBPS_NONE     = 0x0000,  
   PBPS_DELETED  = 0x0001,  
   PBPS_DISABLED = 0x0002,  
   PBPS_ENABLED  = 0x0003  
};  
typedef DWORD PENDING_BP_STATE;  
```  
  
```csharp  
public enum enum_PENDING_BP_STATE {   
   PBPS_NONE     = 0x0000,  
   PBPS_DELETED  = 0x0001,  
   PBPS_DISABLED = 0x0002,  
   PBPS_ENABLED  = 0x0003  
};  
```  
  
## <a name="members"></a>Члены  
 PBPS_NONE  
 Местозаполнитель для нуля. Это значение никогда не возвращается.  
  
 PBPS_DELETED  
 Указывает, что ожидающая точка останова была удалена.  
  
 PBPS_DISABLED  
 Указывает, что запрещено ожидающая точка останова.  
  
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