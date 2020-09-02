---
title: BP_TYPE | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_TYPE
helpviewer_keywords:
- BP_TYPE enumeration
ms.assetid: ef07191e-7966-43ab-96fb-1a0b1db3115d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1a0c479182f1ff9efd4b35f2fed2de35d3536202
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153262"
---
# <a name="bp_type"></a>BP_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Указывает, находится ли точка останова в расположении кода, является расположением данных или другим типом точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum enum_BP_TYPE {   
   BPT_NONE    = 0x0000,  
   BPT_CODE    = 0x0001,  
   BPT_DATA    = 0x0002,  
   BPT_SPECIAL = 0x0003  
};  
typedef DWORD BP_TYPE;  
```  
  
```csharp  
public enum enum_BP_TYPE {   
   BPT_NONE    = 0x0000,  
   BPT_CODE    = 0x0001,  
   BPT_DATA    = 0x0002,  
   BPT_SPECIAL = 0x0003  
};  
```  
  
## <a name="members"></a>Участники  
 BPT_NONE  
 Указывает, что тип точки останова отсутствует.  
  
 BPT_CODE  
 Задает точку останова в коде.  
  
 BPT_DATA  
 Задает точку останова в данных.  
  
 BPT_SPECIAL  
 Указывает точку останова, которая не является ни кодом, ни типом данных. Этот тип является устаревшим и не должен использоваться.  
  
## <a name="remarks"></a>Remarks  
 Передается в качестве параметра методам [жетбреакпоинттипе](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) и [жетбреакпоинттипе](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md) .  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [жетбреакпоинттипе](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)   
 [GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)
