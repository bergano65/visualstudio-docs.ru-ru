---
title: Управление несколькими потоками в управляемом коде | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 296ef23bc512a86917920b3c3d5fbb5ec203a21e
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387022"
---
# <a name="managing-multiple-threads-in-managed-code"></a>Управление несколькими потоками в управляемом коде
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если у вас есть управляемое расширение VSPackage, вызывающее асинхронные методы или имеющее операции, которые выполняются в потоках, отличных от потока пользовательского интерфейса Visual Studio, следуйте инструкциям, приведенным ниже. Можно защитить поток пользовательского интерфейса, поскольку ему не нужно ждать завершения работы в другом потоке. Вы можете сделать код более эффективным, так как у вас нет дополнительных потоков, которые занимают пространство стека, и вы можете сделать его более надежным и простым в отладке, так как избежать взаимоблокировок и нереагирования.  
  
 В общем случае можно переключиться из потока пользовательского интерфейса в другой поток или наоборот. Когда метод возвращает значение, текущий поток является потоком, из которого он был первоначально вызван.  
  
> [!IMPORTANT]
> Следующие рекомендации используют интерфейсы API в <xref:Microsoft.VisualStudio.Threading> пространстве имен, в частности <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> класс. Интерфейсы API в этом пространстве имен являются новыми в [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] . Экземпляр класса можно получить <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> из <xref:Microsoft.VisualStudio.Shell.ThreadHelper> свойства `ThreadHelper.JoinableTaskFactory` .  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>Переключение из потока пользовательского интерфейса в фоновый поток  
  
1. Если вы работаете в потоке пользовательского интерфейса и хотите выполнять асинхронную работу в фоновом потоке, используйте Task. Run ():  
  
    ```csharp  
    await Task.Run(async delegate{  
        // Now you’re on a separate thread.  
    });  
    // Now you’re back on the UI thread.  
  
    ```  
  
2. Если вы работаете в потоке пользовательского интерфейса и хотите синхронно блокироваться при выполнении работы в фоновом потоке, используйте <xref:System.Threading.Tasks.TaskScheduler> свойство `TaskScheduler.Default` внутри <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> :  
  
    ```csharp  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switching-from-a-background-thread-to-the-ui-thread"></a>Переключение из фонового потока в поток пользовательского интерфейса  
  
1. Если вы находитесь в фоновом потоке и хотите сделать что-то в потоке пользовательского интерфейса, используйте <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> :  
  
    ```csharp  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     Для <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> переключения на поток пользовательского интерфейса можно использовать метод. Этот метод отправляет сообщение в поток пользовательского интерфейса с продолжением текущего асинхронного метода, а также взаимодействует с остальной частью платформы потоков, чтобы установить правильный приоритет и избежать взаимоблокировок.  
  
     Если фоновый метод потока не является асинхронным и его нельзя сделать асинхронным, вы по-прежнему можете использовать `await` синтаксис для переключения в поток пользовательского интерфейса путем создания оболочки работы с <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> , как показано в следующем примере:  
  
    ```csharp  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```
