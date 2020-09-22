---
title: Отправка необходимых событий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 457e2daf3e52c23ba9733d09d3aeb94750b5fab9
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2020
ms.locfileid: "90843221"
---
# <a name="sending-the-required-events"></a>Отправка необходимых событий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Используйте эту процедуру для отправки необходимых событий.  
  
## <a name="process-for-sending-required-events"></a>Процесс отправки необходимых событий  
 Следующие события являются обязательными в этом порядке при создании модуля отладки (DE) и присоединении его к программе:  
  
1. Отправка объекта события [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) в Диспетчер отладки сеансов (SDM) при инициализации de для отладки одной или нескольких программ в процессе.  
  
2. Когда отлаживаемая программа прикрепляется к, отправляет объект события [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) в SDM. Это событие может быть остановлено в зависимости от структуры подсистемы.  
  
3. Если программа подключена к при запуске процесса, отправьте объект события [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) в SDM, чтобы уведомить IDE о новом потоке. Это событие может быть остановлено в зависимости от структуры подсистемы.  
  
4. Отправка объекта события [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) в SDM при завершении загрузки отлаживаемой программы или при завершении присоединения к программе. Это событие должно быть событием остановки.  
  
5. Если приложение для отладки запускается, отправляет объект события [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) в SDM, когда первая инструкция кода в архитектуре времени выполнения собирается для выполнения. Это событие всегда является остановкой. При пошаговом выполнении сеанса отладки среда IDE останавливается на этом событии.  
  
> [!NOTE]
> Во многих языках используются глобальные инициализаторы или внешние, предварительно скомпилированные функции (из библиотеки CRT или _Main) в начале своего кода. Если язык отлаживаемой программы содержит один из этих типов элементов перед начальной точкой входа, то выполняется этот код и событие точки входа отправляется при достижении точки входа пользователя, такой как **Main** или `WinMain` .  
  
## <a name="see-also"></a>См. также:  
 [Включение программы для отладки](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
