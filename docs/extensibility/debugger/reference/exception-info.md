---
title: "EXCEPTION_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EXCEPTION_INFO"
helpviewer_keywords: 
  - "Структура EXCEPTION_INFO"
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# EXCEPTION_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Описывает исключение или ошибка во время выполнения, создаваемые отлаживаемой программой.  
  
## Синтаксис  
  
```cpp#  
typedef struct tagEXCEPTION_INFO {   
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   BSTR            bstrExceptionName;  
   DWORD           dwCode;  
   EXCEPTION_STATE dwState;  
   GUID            guidType;  
} EXCEPTION_INFO;  
```  
  
```c#  
public struct EXCEPTION_INFO {   
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public string         bstrExceptionName;  
   public uint           dwCode;  
   public uint           dwState;  
   public Guid           guidType;  
};  
```  
  
## Члены  
 pProgram  
 IDebugProgram2 объект, представляющий программы, в которой произошло исключение.  
  
 bstrProgramName  
 Имя программы, в которой произошло исключение.  
  
 bstrExceptionName  
 Имя исключения.  
  
 dwCode  
 Код идентификации для исключений или ошибок во время выполнения.  
  
 dwState  
 Значение [EXCEPTION\_STATE](../../../extensibility/debugger/reference/exception-state.md) перечисление, указывающее состояние исключения.  
  
 guidType  
 Идентификатор языка, то GUID `guidLang` OR  `guidEng`.  
  
## Заметки  
 Эта структура передается как параметр [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) и  [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) методы.  Эта структура также передается [GetException](../Topic/IDebugExceptionEvent2::GetException.md) метод, который требуется заполнить.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [EXCEPTION\_STATE](../../../extensibility/debugger/reference/exception-state.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)   
 [GetException](../Topic/IDebugExceptionEvent2::GetException.md)