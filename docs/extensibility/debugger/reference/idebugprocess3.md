---
title: "IDebugProcess3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3"
helpviewer_keywords: 
  - "Интерфейс IDebugProcess3"
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# IDebugProcess3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет процесс и его выполнение программы.  Этот интерфейс существует в качестве замены для нескольких методов IDebugProgram2 интерфейс.  Он предоставляет элемент управления по всем программами в процессе.  
  
> [!NOTE]
>  [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)" [Выполнение](../../../extensibility/debugger/reference/idebugprogram2-execute.md)и  [Шаг](../../../extensibility/debugger/reference/idebugprogram2-step.md) методы нерекомендуемый и должны быть больше не используются.  Используйте соответствующие методы `IDebugProcess3` интерфейс.  
  
## Синтаксис  
  
```  
IDebugProcess3 : IDebugProcess2  
```  
  
## Примечания по реализации  
 Этот интерфейс реализуется пользовательским поставщиком порта для управления программы, таких как группа.  Если программы управляемые как группа, можно отслеживать их выполнение и устанавливать язык для средства оценки выражений.  Этот интерфейс должен быть реализован поставщиком порта.  
  
## Замечания для вызывающих объектов  
 Этот интерфейс, вызывается основным сеанса отладки \(SDM\) диспетчер для взаимодействия с группой в составе программы, заданные в этом процессе.  
  
 Вызов [QueryInterface](/visual-cpp/atl/queryinterface) на  [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) интерфейс для получения этого интерфейса.  
  
## Методы в том порядке Vtable  
 Помимо методов, наследуемых из [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)"  `IDebugProcess3` реализует следующие методы.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Продолжает выполнение или пошаговой отладки процесса.|  
|[Выполнение](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Начинает выполнение процесса ".|  
|[Шаг](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Шаг вперед одна инструкция или выписка в процессе.|  
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Получает причину, что процесс запущен для отладки.|  
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Задает язык размещения, так что отладчик сможет загрузить подходящее средство оценки выражений.|  
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Возвращает язык, на данный момент задайте для этого процесса.|  
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Запрещает правку и продолжает \(ENCL\) для этого процесса.<br /><br /> Пользовательский поставщик порта не реализует этот метод \(он должен всегда возвращать `E_NOTIMPL`\).|  
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Получает состояние ENCL для этого процесса.<br /><br /> Пользовательский поставщик порта не реализует этот метод \(он должен всегда возвращать `E_NOTIMPL`\).|  
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Извлекает массив уникальных идентификаторов доступных обработчиков отладки.|  
  
## Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)