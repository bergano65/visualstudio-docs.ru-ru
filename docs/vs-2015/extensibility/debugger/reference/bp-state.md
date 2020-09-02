---
title: BP_STATE | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_STATE
helpviewer_keywords:
- BP_STATE enumeration
ms.assetid: 08aa6a3f-3e5f-4c83-8eca-7b7b5f8e208d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a4de23d462136ad417859d7064fef6b4ace7e59c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153254"
---
# <a name="bp_state"></a>BP_STATE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Задает существование привязанной точки останова, а также указывает, включен ли он.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum enum_BP_STATE {   
   BPS_NONE     = 0x0000,  
   BPS_DELETED  = 0x0001,  
   BPS_DISABLED = 0x0002,  
   BPS_ENABLED  = 0x0003  
};  
typedef DWORD BP_STATE;  
```  
  
```csharp  
public enum enum_BP_STATE {   
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
 Указывает, что точка останова отключена.  
  
 BPS_ENABLED  
 Указывает, что точка останова включена.  
  
## <a name="remarks"></a>Remarks  
 Возвращается методом метода « [State](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md) ».  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)
