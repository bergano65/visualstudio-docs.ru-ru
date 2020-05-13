---
title: Управление программой Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e77e233050c5ce10aef5053f82c8d26cb984b85
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738227"
---
# <a name="program-control"></a>Контроль программы
При отладке Visual Studio все следующие процедуры на уровне программы происходят следующим образом:

- Установка следующего оператора, т.е. настройка компьютера на следующую инструкцию, которая будет выполнена в определенной среде кадра

- Выполнение, то есть продолжение выхода из режима шага

- Переход к следующей инструкции

- Продолжение текущего режима шага

- Приостановка потоков, содержащихся в программе

- Возобновление потоков, содержащихся в программе

> [!NOTE]
> Просмотр стека вызовов реализован на уровне потока. Чтобы перечислить информацию о кадре при просмотре стека вызовов для потока, необходимо реализовать все методы интерфейса [IEnumDebugFrameInfo2.](../../extensibility/debugger/reference/ienumdebugframeinfo2.md)

## <a name="methods-of-program-control"></a>Методы управления программами
 В следующей таблице показаны методы [IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) которые должны быть реализованы для минимально функционального двигателя отладки (DE) и управления выполнением.

|Метод|Описание|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Продолжает работать все потоки, содержащиеся в программе из остановленного состояния. Требуется для контроля выполнения.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Продолжает работать все потоки, содержащиеся в программе из остановленного состояния. Требуется для контроля выполнения.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Выполняет шаг на данном потоке. Продолжает работать все другие потоки, содержащиеся в программе. Требуется для контроля выполнения.|

 Для многопоточных программ необходимо также реализовать метод [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) и все методы интерфейса [IEnumDebugThreads2.](../../extensibility/debugger/reference/ienumdebugthreads2.md)

## <a name="see-also"></a>См. также
- [Контроль исполнения и государственная оценка](../../extensibility/debugger/execution-control-and-state-evaluation.md)
