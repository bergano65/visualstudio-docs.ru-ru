---
title: "IDebugModule2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule2"
helpviewer_keywords: 
  - "Интерфейс IDebugModule2"
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugModule2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет модуль\-что, исполнительная единица измерения программа\-такого в виде библиотеки DLL.  
  
## Синтаксис  
  
```  
IDebugModule2 : IUnknown  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) реализует этот интерфейс, чтобы представить модуль и обеспечить доступ к сведениям об этом модуле.  
  
## Замечания для вызывающих объектов  
 Вызов [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) возвращает данный интерфейс.  DE отправляет [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) интерфейс к сеансу отладки \(SDM\) с помощью диспетчера  [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) метод.  
  
 Этот интерфейс может также возвращать в выражении [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структура \(которую возвращает вызовом  [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)\).  
  
 [Далее](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) возвращает также интерфейс \([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) возвращает  [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) интерфейс\).  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugModule2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Возвращает [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) описывает то этот модуль.|  
|[ReloadSymbols\_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|УСТАРЕЛ.  НЕ ИСПОЛЬЗУЙТЕ.  Перезагрузить символов для этого модуля.|  
  
## Заметки  
 Данные могут отображаться в модуля **Модули** окно интегрированной среды разработки.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)