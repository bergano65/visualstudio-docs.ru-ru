---
title: "IDebugCodeContext2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCodeContext2"
helpviewer_keywords: 
  - "Интерфейс IDebugCodeContext2"
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugCodeContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет начальную позицию инструкции кода.  Для большинства архитектур времени выполнения, сегодня контекст кода можно рассматривать как адреса в потоке выполнения программы.  
  
## Синтаксис  
  
```  
IDebugCodeContext2 : IDebugMemoryContext2  
```  
  
## Примечания по реализации  
 Отладчик реализующий этот интерфейс, чтобы связать позиция инструкции кода в позиции документа.  
  
## Замечания для вызывающих объектов  
 Методы во многих интерфейсы возвращают этот интерфейс, обычно [GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md).  Кроме того, широко используется с [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) интерфейс так же, как в данных о разрешениях точки останова.  
  
## Методы в том порядке Vtable  
 в дополнение к методам на [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) интерфейс этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md)|Возвращает контекст документа, соответствующий активный контекст кода.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Получает сведения о языке для этого контекста кода.|  
  
## Заметки  
 Ключевое различие между `IDebugCodeContext2` интерфейс и  [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) интерфейс, который  `IDebugCodeContext2` всегда инструкци\-выравнивает.  Это означает, что `IDebugCodeContext2` всегда указывает на начало инструкции, тогда как  `IDebugMemoryContext2` может указывать на любой байту памяти в архитектуре среды выполнения.  `IDebugCodeContext2` увеличивает инструкциям, а не размер базового хранилища \(обычно байтом\).  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [CanSetNextStatement](../Topic/IDebugThread2::CanSetNextStatement.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)   
 [GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md)   
 [Далее](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)