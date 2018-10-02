---
title: BP_STATE | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_STATE
helpviewer_keywords:
- BP_STATE enumeration
ms.assetid: 08aa6a3f-3e5f-4c83-8eca-7b7b5f8e208d
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f6fc9cdcdedb9b733da27489232558f394879cc1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571552"
---
# <a name="bpstate"></a>BP_STATE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [BP_STATE](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/bp-state).  
  
Задает существование связанная точка останова, а также указывает, включена ли.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum enum_BP_STATE {   
   BPS_NONE     = 0x0000,  
   BPS_DELETED  = 0x0001,  
   BPS_DISABLED = 0x0002,  
   BPS_ENABLED  = 0x0003  
};  
typedef DWORD BP_STATE;  
```  
  
```csharp  
public enum enum_BP_STATE {   
   BPS_NONE     = 0x0000,  
   BPS_DELETED  = 0x0001,  
   BPS_DISABLED = 0x0002,  
   BPS_ENABLED  = 0x0003  
};  
```  
  
## <a name="members"></a>Участники  
 BPS_NONE  
 Указывает, что точка останова не существует.  
  
 BPS_DELETED  
 Указывает, что точка останова была удалена.  
  
 BPS_DISABLED  
 Указывает, что точка останова отключен.  
  
 BPS_ENABLED  
 Указывает, что точка останова включена.  
  
## <a name="remarks"></a>Примечания  
 Возвращаемые [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)

