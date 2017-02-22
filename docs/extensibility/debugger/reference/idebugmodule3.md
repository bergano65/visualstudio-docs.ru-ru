---
title: "IDebugModule3 | Microsoft Docs"
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
  - "IDebugModule3"
helpviewer_keywords: 
  - "Интерфейс IDebugModule3"
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugModule3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет модуль, который поддерживает другие расположения символов и состояний JustMyCode.  
  
## Синтаксис  
  
```  
IDebugModule3 : IDebugModule2  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) реализует этот интерфейс, чтобы поддерживать другие расположения символов и работать с состояниями JustMyCode \(см. [Глоссарий отладчика Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) для определения "JustMyCode"\).  
  
## Замечания для вызывающих объектов  
 Вызов [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) возвращает данный интерфейс.  DE отправляет [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) интерфейс к сеансу отладки \(SDM\) с помощью диспетчера  [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) метод.  Кроме того, вызов [QueryInterface](/visual-cpp/atl/queryinterface) на  [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) интерфейс возвращает этот интерфейс.  
  
## Методы в том порядке Vtable  
 в дополнение к методам на IDebugModule2 интерфейс этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Возвращает список путей, которые выполняют поиск символов и результатов поиска каждый путь.|  
|[LoadSymbols](../Topic/IDebugModule3::LoadSymbols.md)|Загружает и инициализируют символов для текущего модуля.|  
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Возвращает пометить, указывающее, представляет ли модуль кода пользователя.|  
|[SetJustMyCodeState](../Topic/IDebugModule3::SetJustMyCodeState.md)|Определяет, должен ли модуль быть кодом пользователя или не учитывается.|  
  
## Заметки  
 Visual Studio обычным объект\-получатель этого интерфейса.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)