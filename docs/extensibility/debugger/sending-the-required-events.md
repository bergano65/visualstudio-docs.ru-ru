---
title: "Отправка событий требуется | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 30a5b1150d44c138465db36da2b032b71f075397
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="sending-the-required-events"></a>Отправка необходимых событий
Эта процедура используется для отправки требуемые события.  
  
## <a name="process-for-sending-required-events"></a>Процесс отправки необходимые события  
 В указанном порядке, при создании отладочной ядра (DE) и подключение к программе необходимы следующие события:  
  
1.  Отправить [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) объект события для диспетчера сеанса отладки (SDM), при инициализации DE для одной или нескольких программ в процессе отладки.  
  
2.  При присоединении к отлаживаемой программы, отправить [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) SDM объекта события. Это событие может быть события остановки, в зависимости от макета ядра.  
  
3.  Если программа прикреплен к при запуске процесса, отправить [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) объект SDM для уведомления IDE новый поток событий. Это событие может быть события остановки, в зависимости от макета ядра.  
  
4.  Отправить [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) объект события для SDM при завершении загрузки или после завершения присоединения к программе отлаживаемой программы. Это событие должно быть событие остановки.  
  
5.  При запуске приложения для отладки, отправлять [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) объект события для SDM при будет выполнена первая инструкция кода в архитектуры во время выполнения. Это событие всегда является остановка. При отладке в сеансе отладки интегрированной среды разработки останавливается на это событие.  
  
> [!NOTE]
>  Многие языки использовать глобальные инициализаторы или внешние предкомпилированного функции (от библиотеки CRT или _Main) в начале кода. Если язык программы отладки содержит один из этих типов элементов до момента начальной операции, этот код запускается и отправляется событие точки входа при пользователя точки входа, такие как **основной** или `WinMain`, достигнут.  
  
## <a name="see-also"></a>См. также  
 [Включение программы для отладки](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)