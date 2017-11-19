---
title: "MESSAGETYPE | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MESSAGETYPE
helpviewer_keywords: MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7cbb3ddd27c7cbb92c7e248c5091d6fe0e21dc3e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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
  
## <a name="members"></a>Члены  
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