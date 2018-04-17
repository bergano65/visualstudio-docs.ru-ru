---
title: MESSAGETYPE | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3fa09d938e0e7c3853431369c7e0634242df2ee0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="messagetype"></a>MESSAGETYPE
Указывает тип сообщения и его причины.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
typedef DWORD MESSAGETYPE;  
```  
  
```csharp  
public enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
```  
  
## <a name="members"></a>Участники  
 MT_OUTPUTSTRING  
 Указывает, что сообщения должны отправляться в окне вывода. Это взаимно исключают друг друга из `MT_MESSAGEBOX`.  
  
 MT_MESSAGEBOX  
 Указывает, что сообщение должно отображаться в окне сообщения. Это взаимно исключают друг друга из `MT_OUTPUTSTRING`.  
  
 MT_TYPE_MASK  
 Значение маски для изоляции места назначения сообщения.  
  
 MT_REASON_EXCEPTION  
 Указывает, в результате исключения отображается окно сообщения. Это взаимно исключают друг друга из `MT_REASON_TRACEPOINT`.  
  
 MT_REASON_TRACEPOINT  
 Указывает, в результате обращения к точке трассировки отображается окно сообщения. Это взаимно исключают друг друга в `MT_REASON_EXCEPTION`.  
  
 MT_REASON_MASK  
 Значение маски для изоляции причина показывается сообщение.  
  
## <a name="remarks"></a>Примечания  
 Эти значения возвращаются из [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) и [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) методы.  
  
 Одно из значений, причины могут быть объединены с одним из значений выходных данных назначения, с помощью побитовой операции `OR`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)