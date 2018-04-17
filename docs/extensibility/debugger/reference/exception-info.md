---
title: EXCEPTION_INFO | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c48772ed5835daeff9d47773e6e48526993fa425
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="exceptioninfo"></a>EXCEPTION_INFO
Описывает исключения или ошибки во время выполнения вызванных отлаживаемой программы.  
  
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
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) объект, представляющий программу, в которой возникло исключение.  
  
 bstrProgramName  
 Имя программы, в которой возникло исключение.  
  
 bstrExceptionName  
 Имя исключения.  
  
 dwCode  
 Идентификационный код ошибки исключения или во время выполнения.  
  
 dwState  
 Значение из [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) перечисление, определяющее состояние исключения.  
  
 guidType  
 Идентификатор GUID языка, либо `guidLang` или `guidEng`.  
  
## <a name="remarks"></a>Примечания  
 Эта структура передается как параметр [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) и [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) методы. Эта структура также передается [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) метод, чтобы быть заполнено.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)   
 [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)