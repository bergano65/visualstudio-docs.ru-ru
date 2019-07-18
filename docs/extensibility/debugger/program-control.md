---
title: Программы управления | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a19769925689ae8131c6443ab80ccefeefa82290
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351444"
---
# <a name="program-control"></a>Управление программой
В Visual Studio отладки, все следующие пошагового выполнения и продолжая подпрограммы происходят на уровне программы.

- Установка следующего оператора, то есть Настройка компьютера следующей инструкции для выполнения в среде определенный кадр

- Выполнение, то есть продолжать выйти из режима пошагового выполнения

- Пошаговое выполнение следующей инструкции

- Продолжить текущий режим пошагового выполнения

- Приостановка потоков, содержащихся в программе

- Возобновление работы потоков, содержащихся в программе

> [!NOTE]
> Просмотр стека вызовов реализуется на уровне потока. Чтобы перечислить сведения о кадре, при просмотре стек вызовов для потока, должен реализовывать все методы объекта [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) интерфейс.

## <a name="methods-of-program-control"></a>Методы управления в программе
 В следующей таблице показаны методы [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , должен быть реализован для модуля простейшей функциональной отладки (DE) и управление выполнением.

|Метод|Описание|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Продолжает выполнение всех потоков, содержащихся в какой-либо программой в остановленном состоянии. Требуется для выполнения элемента управления.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Продолжает выполнение всех потоков, содержащихся в какой-либо программой в остановленном состоянии. Требуется для выполнения элемента управления.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Выполняет шаг в данном потоке. Продолжает выполнение всех потоков, содержащихся в программе. Требуется для выполнения элемента управления.|

 Для многопоточных программ, необходимо также реализовать [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) метод и все методы объекта [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) интерфейс.

## <a name="see-also"></a>См. также
- [Выполнение управления и состояние оценки](../../extensibility/debugger/execution-control-and-state-evaluation.md)