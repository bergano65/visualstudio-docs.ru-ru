---
title: "IDebugEngine2 | Microsoft Docs"
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
  - "IDebugEngine2"
helpviewer_keywords: 
  - "Интерфейс IDebugEngine2"
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет обработчик отладки \(DE\).  Он используется для управления различными аспектами сеанса отладки, от точки останова для установки и снятия исключения.  
  
## Синтаксис  
  
```  
IDebugEngine2 : IUnknown  
```  
  
## Примечания по реализации  
 Этот интерфейс реализуется настраиваемым средством DE для управления отладка программ.  Этот интерфейс должен быть реализован DE.  
  
## Замечания для вызывающих объектов  
 Этот интерфейс, вызывается сеанса отладки \(SDM\) диспетчер для управления сеанс отладки, включая управление исключения создать точки останова и реагирование на события, переданного DE синхронным.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugEngine2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Создает перечислитель для всех программ, отлаживанными DE.|  
|[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Вложение DE в программе.|  
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Создает отложенную точку останова в DE.|  
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Определяет, как DE должен обрабатывать данного исключения.|  
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Удаляет указанное исключение, поэтому он больше не обрабатывается обработчиком отладки.|  
|[RemoveAllSetExceptions](../Topic/IDebugEngine2::RemoveAllSetExceptions.md)|Удаляет список исключений интегрированная среда разработки есть набор для заданной архитектуры или языка среды выполнения.|  
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Получает GUID DE.|  
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Информирует DE, что указанная программа нетипово была завершена и DE должен очистки всех ссылок к программе и отправить программу удаляет событие.|  
|[ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md)|SDM был получен при вызове и обрабатывается для указания того, что синхронные отладочные события, отправленное DE к SDM, ранее.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Устанавливает языковой стандарт DE.|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Задает корневой элемент реестра в данный момент занято DE.|  
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Определяет метрику.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Запросы, которые все программы, отлаживанными этим DE остановить выполнение в следующий раз один из них потоков пытаются выполнить.|  
  
## Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)