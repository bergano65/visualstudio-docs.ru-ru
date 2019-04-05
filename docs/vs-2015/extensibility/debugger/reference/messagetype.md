---
title: MESSAGETYPE | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c17564c992f4c8855d8a96165975a5d0e132755c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991044"
---
# <a name="messagetype"></a>MESSAGETYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Указывает тип сообщения и причины.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum enum_MESSAGETYPE {   
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
public enum enum_MESSAGETYPE {   
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
 Указывает, что сообщения должны быть видны в окне сообщения. Это взаимно исключают друг друга из `MT_OUTPUTSTRING`.  
  
 MT_TYPE_MASK  
 Значение маски для изоляции назначения для сообщения.  
  
 MT_REASON_EXCEPTION  
 Указывает, что окно сообщения отображается в результате исключения. Это взаимно исключают друг друга из `MT_REASON_TRACEPOINT`.  
  
 MT_REASON_TRACEPOINT  
 Указывает, что в результате обращения к точке трассировки отображается окно сообщения. Это взаимно исключают друг друга для `MT_REASON_EXCEPTION`.  
  
 MT_REASON_MASK  
 Значение маски для изоляции причина для отображаемого сообщения.  
  
## <a name="remarks"></a>Примечания  
 Эти значения возвращаются из [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) и [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) методы.  
  
 Одно из значений причина могут сочетаться с одним из значений назначения выходных данных при помощи побитовой `OR`.  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
