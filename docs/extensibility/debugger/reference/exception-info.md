---
title: EXCEPTION_INFO | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e255695cd461f5c272bc65f695d8935ab892d034
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54960247"
---
# <a name="exceptioninfo"></a>EXCEPTION_INFO
Описывает исключение или ошибка времени выполнения, выводится отлаживаемой программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct tagEXCEPTION_INFO {   
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   BSTR            bstrExceptionName;  
   DWORD           dwCode;  
   EXCEPTION_STATE dwState;  
   GUID            guidType;  
} EXCEPTION_INFO;  
```  
  
```csharp  
public struct EXCEPTION_INFO {   
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public string         bstrExceptionName;  
   public uint           dwCode;  
   public uint           dwState;  
   public Guid           guidType;  
};  
```  
  
## <a name="members"></a>Участники  
 pProgram  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) объект, представляющий программу, в котором произошло исключение.  
  
 bstrProgramName  
 Имя программы, в котором произошло исключение.  
  
 bstrExceptionName  
 Имя исключения.  
  
 dwCode  
 Идентификационный код ошибки исключения или во время выполнения.  
  
 dwState  
 Значение из [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) перечисление, определяющее состояние исключения.  
  
 guidType  
 Идентификатор GUID языка, либо `guidLang` или `guidEng`.  
  
## <a name="remarks"></a>Примечания  
 Эта структура передается в качестве параметра [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) и [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) методы. Эта структура также передается [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) метод для заполнения.  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)   
 [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)