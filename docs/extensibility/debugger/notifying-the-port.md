---
title: "Уведомление порт | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "порты, уведомления"
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Уведомление порт
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

После запуска программы порт должен уведомить следующим образом:  
  
1.  Если порт возвращает новый узел программы, он отправляет событие создания программы обратно к сеансу отладки.  Событие передает с ним интерфейс, который представляет программу.  
  
2.  Запросы сеанса отладки программы для идентификатора обработчика отладки \(DE\), который можно вложить.  
  
3.  Сеанс отладки проверяет наличие DE в списке допустимого DEs для этой программы.  Сеанс отладки получает этот список из параметров активной программы решения, переданных ему изначально пакетом отладки.  
  
     DE должен находиться на позволяемом списке или же DE не будет вложен в программе.  
  
 Программно, если порт сначала возвращает новый узел, он создает программы IDebugProgram2 интерфейс для представления программу.  
  
> [!NOTE]
>  Это не следует путать с `IDebugProgram2` интерфейс, созданный в дальнейшем обработчик отладки \(DE\).  
  
 Порт отправляет [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) событие создания программы обратно к сеансу отладки \(SDM\) посредством диспетчера модели COM  `IConnectionPoint` интерфейс.  
  
> [!NOTE]
>  Это не следует путать с `IDebugProgramCreateEvent2` интерфейс, который передается позже DE.  
  
 Вместе с интерфейсом данного события, порт отправляет [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)"  [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)и  [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) интерфейсы, которые представляют порт, процесс и программы соответственно.  Вызовы SDM [IDebugProgram2:: GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) получить идентификатор GUID DE, который может отлаживать программы.  Идентификаторы GUID исходных было получено из IDebugProgramNode2 интерфейс.  
  
 SDM проверяет наличие DE в списке допустимого DEs.  SDM получает этот список из параметров активной программы решения, переданных ему изначально пакетом отладки.  DE должен находиться на позволяемом списке или он не будет вложен в программе.  
  
 DE известен только идентификатор, SDM готов вложить его в программе.  
  
## См. также  
 [Запуск программы](../../extensibility/debugger/launching-a-program.md)   
 [Присоединение после запуска](../../extensibility/debugger/attaching-after-a-launch.md)   
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)