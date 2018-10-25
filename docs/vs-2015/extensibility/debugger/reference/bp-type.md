---
title: BP_TYPE | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_TYPE
helpviewer_keywords:
- BP_TYPE enumeration
ms.assetid: ef07191e-7966-43ab-96fb-1a0b1db3115d
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 14f8aba4ca1bc46df2c2322fde842017f1fbd45f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919602"
---
# <a name="bptype"></a>BP_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Определяет точку останова в месте кода, — это расположение данных или — еще один тип точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum enum_BP_TYPE {   
   BPT_NONE    = 0x0000,  
   BPT_CODE    = 0x0001,  
   BPT_DATA    = 0x0002,  
   BPT_SPECIAL = 0x0003  
};  
typedef DWORD BP_TYPE;  
```  
  
```csharp  
public enum enum_BP_TYPE {   
   BPT_NONE    = 0x0000,  
   BPT_CODE    = 0x0001,  
   BPT_DATA    = 0x0002,  
   BPT_SPECIAL = 0x0003  
};  
```  
  
## <a name="members"></a>Участники  
 BPT_NONE  
 Указывает тип точки останова не.  
  
 BPT_CODE  
 Задает точку останова кода.  
  
 BPT_DATA  
 Задает точку останова по данным.  
  
 BPT_SPECIAL  
 Задает точку останова, которая не является ни код, ни тип данных. Этот тип является устаревшим и не должны использоваться.  
  
## <a name="remarks"></a>Примечания  
 Переданный в качестве параметра для [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) и [GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md) методы.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)   
 [GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)

