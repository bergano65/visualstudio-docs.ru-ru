---
title: Отправка необходимых событий | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d1a3803b12c2941f9e76d1bb97d5885940197192
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571707"
---
# <a name="sending-the-required-events"></a>Отправка необходимых событий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [отправляется пакет событий требуется](https://docs.microsoft.com/visualstudio/extensibility/debugger/sending-the-required-events).  
  
Эта процедура используется для отправки необходимые события.  
  
## <a name="process-for-sending-required-events"></a>Процесс отправки необходимые события  
 В указанном порядке, при создании отладочной ядра (DE) и подключите его к программе необходимы следующие события:  
  
1.  Отправить [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) объект события, чтобы диспетчер отладки сеансов (SDM), при инициализации DE для одной или нескольких программ в процессе отладки.  
  
2.  При присоединении к программе для отладки, отправлять [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) объект события для SDM. Это событие может быть событие stopping, в зависимости от макета ядра.  
  
3.  Если программа будет подключен к при запуске процесса, отправить [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) объект события для SDM для уведомления IDE по новому потоку. Это событие может быть событие stopping, в зависимости от макета ядра.  
  
4.  Отправить [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) объект события для SDM при завершении загрузки или после завершения присоединения к программе отлаживаемой программы. Это событие должно быть событии остановки.  
  
5.  При запуске приложения для отладки, отправлять [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) объект события для SDM, должна быть выполнена при первой инструкции кода в архитектуре во время выполнения. Это событие всегда является событием остановки. При пошаговом выполнении в сеанс отладки, интегрированной среды разработки останавливается на это событие.  
  
> [!NOTE]
>  Многие языки использовать глобальные инициализаторы или внешних, предварительно скомпилированных функций (из библиотеки CRT или "_main") в начале кода. Если язык программы отладки содержит любой из этих типов элементов перед начальной отправной точкой, выполняется этот код и отправляется событие точки входа при пользователя точки входа, такие как **основной** или `WinMain`, достигнут.  
  
## <a name="see-also"></a>См. также  
 [Включение программы для отладки](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)

