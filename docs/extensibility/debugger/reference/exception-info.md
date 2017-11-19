---
title: "EXCEPTION_INFO | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EXCEPTION_INFO
helpviewer_keywords: EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8bb60642857f0f07562feffe7b48e0454a73097e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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
  
## <a name="members"></a>Члены  
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