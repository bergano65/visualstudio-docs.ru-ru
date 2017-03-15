---
title: "Практическое руководство: управление несколькими потоками в управляемом коде | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 477f57bbca9c49e7d7d13155fc1f6e55ee4667a8
ms.openlocfilehash: 417dc6e5285859424dfa3b482a90f1a141cff163
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-managing-multiple-threads-in-managed-code"></a>Практическое руководство: управление несколькими потоками в управляемом коде
Если управляемое расширение VSPackage, который вызывает асинхронный метод или имеет операций, которые выполняются в потоках, отличных от потока пользовательского интерфейса Visual Studio, необходимо соблюдать правила, приведенные ниже. Поток пользовательского интерфейса позволяет исключить отвечает на запросы, поскольку не является необходимым для работы ожидание завершения другого потока. Код можно сделать более эффективным, поскольку не имеют дополнительные потоки, которые занимают пространство стека, и его можно сделать более надежным и простым для отладки, так как избежать взаимоблокировок и зависаний.  
  
 Как правило, можно переключаться из потока пользовательского интерфейса на другой поток или наоборот. При возвращении метода текущий поток является поток, из которого он изначально был вызван.  
  
> [!IMPORTANT]
>  Следующие рекомендации использовать интерфейсы API в пространстве <xref:Microsoft.VisualStudio.Threading>имен, в частности, <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>класс.</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> </xref:Microsoft.VisualStudio.Threading> API-интерфейсы в этом пространстве имен являются новыми в [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]. Можно получить экземпляр <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>из <xref:Microsoft.VisualStudio.Shell.ThreadHelper>Свойства `ThreadHelper.JoinableTaskFactory`.</xref:Microsoft.VisualStudio.Shell.ThreadHelper> </xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>Переключение из потока пользовательского интерфейса в фоновый поток  
  
1.  Если вы хотите сделать асинхронной работы в фоновом потоке в потоке пользовательского интерфейса, используйте Task.Run():  
  
    ```c#  
    await Task.Run(async delegate{  
        // Now you’re on a separate thread.  
    });  
    // Now you’re back on the UI thread.  
  
    ```  
  
2.  Если вы являетесь в потоке пользовательского интерфейса, и нужно заблокировать синхронно, при выполнении работы в фоновом потоке, используйте <xref:System.Threading.Tasks.TaskScheduler>свойство `TaskScheduler.Default` внутри <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> </xref:System.Threading.Tasks.TaskScheduler>  
  
    ```c#  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switching-from-a-background-thread-to-the-ui-thread"></a>Переключение из фонового потока в поток пользовательского интерфейса  
  
1.  Если вы в фоновом потоке, и вы хотите сделать что-нибудь в потоке пользовательского интерфейса, используйте <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>  
  
    ```c#  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     Можно использовать <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>метода, чтобы переключиться в потоке пользовательского интерфейса.</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> Этот метод отправляет сообщение в потоке пользовательского интерфейса с продолжением текущей асинхронного метода, а также обменивается данными с остальной частью потоков платформу, чтобы установить правильный приоритет и избежать взаимоблокировок.  
  
     Если невозможно сделать асинхронным не асинхронный метод фонового потока, можно использовать `await` синтаксис, чтобы переключиться в поток пользовательского интерфейса путем заключения работу с <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>, как показано в этом примере:</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>  
  
    ```c#  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```
