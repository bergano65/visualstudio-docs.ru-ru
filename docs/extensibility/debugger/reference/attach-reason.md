---
title: "ATTACH_REASON | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ATTACH_REASON
helpviewer_keywords: ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ba7149d13c85ec99128488e7207a5320f93d680f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="attachreason"></a>ATTACH_REASON
Указывает причину для модуля отладки (DE) для присоединения к программе узла.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
typedef DWORD ATTACH_REASON;  
```  
  
```csharp  
public enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
```  
  
## <a name="members"></a>Члены  
 ATTACH_REASON_AUTO  
 Присоедините, поскольку процесс в настоящее время находится в режиме отладки.  
  
 ATTACH_REASON_LAUNCH  
 Присоедините, так как был запущен процесс.  
  
 ATTACH_REASON_USER  
 Подключите из-за запроса пользователя.  
  
## <a name="remarks"></a>Примечания  
 Эти значения используются в качестве параметра [присоединение](../../../extensibility/debugger/reference/idebugengine2-attach.md) и [присоединение](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) методы.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Присоединение](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)