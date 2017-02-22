---
title: "THREADPROPERTIES | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "THREADPROPERTIES"
helpviewer_keywords: 
  - "Структура THREADPROPERTIES"
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# THREADPROPERTIES
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Описывает свойства потока.  
  
## Синтаксис  
  
```cpp#  
typedef struct _tagTHREADPROPERTIES {   
   THREADPROPERTY_FIELDS dwFields;  
   DWORD                 dwThreadId;  
   DWORD                 dwSuspendCount;  
   DWORD                 dwThreadState;  
   BSTR                  bstrPriority;  
   BSTR                  bstrName;  
   BSTR                  bstrLocation;  
} THREADPROPERTIES;  
```  
  
```c#  
public struct THREADPROPERTIES {   
   public uint   dwFields;  
   public uint   dwThreadId;  
   public uint   dwSuspendCount;  
   public uint   dwThreadState;  
   public string bstrPriority;  
   public string bstrName;  
   public string bstrLocation;  
};  
```  
  
## Члены  
 dwFields  
 Комбинация из пометит [THREADPROPERTY\_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) перечисление, описывающее, какие поля в этой структуре допустимым.  
  
 dwThreadId  
 Идентификатор потока.  
  
 dwSuspendCount  
 Поток приостанавливается число.  
  
 dwThreadState  
 Значение [СОСТОЯНИЯ ПОТОКА](../../../extensibility/debugger/reference/threadstate.md) перечисление, указывающее состояние потока operating.  
  
 bstrPriority  
 Строка, указывающая приоритет потока. например, "для обычного", "Обычным" или "время" критическим.  
  
 bstName  
 Имя потока.  
  
 bstrLocation  
 Расположение потока \(обычно является самым верхним кадром стека\), обычно выраженное как имя метода, где выполнение в данный момент прерывании работы.  
  
## Заметки  
 Эта структура заполняемую вызовом [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) метод.  Таким образом, возвращаемые сведения обычно используется для заполнения **потоки** окна.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY\_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [СОСТОЯНИЯ ПОТОКА](../../../extensibility/debugger/reference/threadstate.md)