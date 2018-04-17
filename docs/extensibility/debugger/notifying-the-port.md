---
title: Уведомление порт | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1420ca8768ddf1eaedc0d515810bc88b3491c4db
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="notifying-the-port"></a>Уведомление порт
После запуска программы, порт должен получить напоминание, следующим образом:  
  
1.  Порт, получив новый узел программы, он отправляет события создания программы в сеанс отладки. Это событие означает интерфейс, который представляет программу.  
  
2.  Сеанс отладки запрашивает программа для идентификатора модуля отладки (DE), которая может добавить.  
  
3.  Сеанс отладки проверяет, находится ли DE в списке допустимых DEs для этой программы. Этот список возвращает сеанс отладки из параметры активную программу решения, изначально переданные ему отладочный пакет.  
  
     DE должен быть в списке допустимых, иначе DE не может быть присоединен к программе.  
  
 Программным образом, при порт сначала получает новый узел программы, он создает [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) интерфейс для представления программы.  
  
> [!NOTE]
>  Это не следует путать с `IDebugProgram2` интерфейса, созданные модуль отладки (DE) в более поздней версии.  
  
 Отправляет порт [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) события создания программы диспетчеру сеанса отладки (SDM) с помощью COM `IConnectionPoint` интерфейса.  
  
> [!NOTE]
>  Это не следует путать с `IDebugProgramCreateEvent2` интерфейс, который отправляется DE позже.  
  
 А также сам интерфейс событий, отправляет порт [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md), и [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) интерфейсы, которые представляют порт, обрабатывать, и Программа, соответственно. Вызовы SDM [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) для получения идентификатора GUID DE, который можно отлаживать программы. Идентификатор GUID изначально была получена с [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) интерфейса.  
  
 SDM проверяет, находится ли DE в списке допустимых DEs. Параметры активную программу решения, изначально переданные ему отладочный пакет SDM получает этот список. DE должен быть в списке допустимых, иначе он не будет присоединен к программе.  
  
 После получения удостоверения DE SDM готов присоединить ее к программе.  
  
## <a name="see-also"></a>См. также  
 [Запуск программы](../../extensibility/debugger/launching-a-program.md)   
 [Присоединение после запуска](../../extensibility/debugger/attaching-after-a-launch.md)   
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)