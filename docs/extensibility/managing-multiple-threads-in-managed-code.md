---
title: "Как: управление несколькими потоками в управляемом коде | Документы Microsoft"
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 21fcc9388b40baa9e003b4beb876ba2f0f23fbaf
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="how-to-managing-multiple-threads-in-managed-code"></a>Как: управление несколькими потоками в управляемом коде
Если у вас есть расширение управляемого VSPackage, который вызывает асинхронный метод или имеет операций, которые выполняются в потоках, отличных от потоков пользовательского интерфейса Visual Studio, необходимо соблюдать правила, приведены ниже. Поток пользовательского интерфейса может обеспечивать отклик, так как его не нужно подождать, в другом потоке для выполнения. Код можно сделать более эффективен, так как нет дополнительных потоков, которые занимают место в стеке и может сделать его более надежным и простым для отладки, так как позволяет избежать взаимоблокировки и зависаний.  
  
 Как правило, можно переключиться из потока пользовательского интерфейса на другой поток или наоборот. При возвращении метода текущий поток является поток, из которого он изначально был вызван.  
  
> [!IMPORTANT]
>  Следующие рекомендации использовать интерфейсы API в <xref:Microsoft.VisualStudio.Threading> пространства имен, в частности, <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> класса. API-интерфейсы в этом пространстве имен являются новыми в [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]. Можно получить экземпляр <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> из <xref:Microsoft.VisualStudio.Shell.ThreadHelper> свойства `ThreadHelper.JoinableTaskFactory`.  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>Переключение из потока пользовательского интерфейса в фоновый поток  
  
1.  Если необходимо сделать асинхронной работы в фоновом потоке в потоке пользовательского интерфейса, используйте Task.Run():  
  
    ```csharp  
    await Task.Run(async delegate{  
        // Now you're on a separate thread.  
    });  
    // Now you're back on the UI thread.  
  
    ```  
  
2.  Если вы являетесь в потоке пользовательского интерфейса, и вам необходимо заблокировать синхронно, во время работы в фоновом потоке, используйте <xref:System.Threading.Tasks.TaskScheduler> свойство `TaskScheduler.Default` внутри <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:  
  
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
  
1.  Если вы в фоновом потоке, и вы хотите сделать что-нибудь в потоке пользовательского интерфейса, используйте <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:  
  
    ```csharp  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     Можно использовать <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> метод, чтобы переключиться в поток пользовательского интерфейса. Этот метод отправляет сообщение в поток пользовательского интерфейса с продолжением текущего асинхронного метода, а также взаимодействует с остальной частью потоков платформу, чтобы установить правильный приоритет и избежать взаимоблокировок.  
  
     Если нельзя сделать асинхронной не асинхронный метод фонового потока, можно использовать `await` синтаксис, чтобы переключиться в поток пользовательского интерфейса путем заключения работу с <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>, как показано в этом примере:  
  
    ```csharp  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```
