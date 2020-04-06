---
title: 'Как: Управление несколькими потоками в управляемом коде (ru) Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ceaa0af4f57fe374cf9cf4b2dd8b4f40af74a852
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702785"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>Как управлять несколькими потоками в управляемом коде
Если у вас есть управляемое расширение VSPackage, которое вызывает асинхронные методы или имеет операции, которые выполняются на потоках, отличных от потока visual Studio, вы должны следовать приведенным ниже рекомендациям. Вы можете сохранить поток uI отзывчивым, поскольку ему не нужно ждать работы над другим потоком для завершения. Вы можете сделать свой код более эффективным, потому что у вас нет дополнительных потоков, которые занимают пространство стека, и вы можете сделать его более надежным и легче отладить, потому что вы избежать тупиков и зависает.

 Как правило, можно переключиться с потока uI на другой поток или наоборот. Когда метод возвращается, текущий поток представляет собой поток, из которого он первоначально был вызван.

> [!IMPORTANT]
> Следующие руководящие принципы используют <xref:Microsoft.VisualStudio.Threading> AA в пространстве <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> имен, в частности, в классе. AA в этом пространстве имен [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]являются новыми в . Вы можете получить экземпляр <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> из <xref:Microsoft.VisualStudio.Shell.ThreadHelper> `ThreadHelper.JoinableTaskFactory`собственности .

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>Переключение с потока uI в фоновом потоке

1. Если вы находитесь на потоке uI и хотите выполнять асинхронную работу на фоновом потоке, используйте: `Task.Run()`

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. Если вы находитесь на потоке uI и хотите синхронно блокировать во время <xref:System.Threading.Tasks.TaskScheduler> `TaskScheduler.Default` выполнения <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>работ ы на фоновом потоке, используйте свойство внутри:

    ```csharp
    // using Microsoft.VisualStudio.Threading;
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        await TaskScheduler.Default;
        // You're now on a separate thread.
        DoSomethingSynchronous();
        await OrSomethingAsynchronous();
    });
    ```

## <a name="switch-from-a-background-thread-to-the-ui-thread"></a>Переключение с фонового потока на поток uI

1. Если вы находитесь на фоновом потоке и хотите сделать <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>что-то на потоке uI, используйте:

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     Можно использовать <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> метод для переключения на поток uI. Этот метод размещает сообщение в потоке uI с продолжением текущего асинхронного метода, а также общается с остальной частью платформы потоков, чтобы установить правильный приоритет и избежать взаимоблокировки.

     Если метод фонового потока не асинхронный и вы не можете сделать его `await` асинхронным, вы все равно можете <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>использовать синтаксис для переключения на поток uI, обернув работу с, как в этом примере:

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```
