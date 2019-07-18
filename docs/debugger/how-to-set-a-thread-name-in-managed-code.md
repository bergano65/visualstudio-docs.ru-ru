---
title: Практическое руководство. Установка имени потока в управляемом коде | Документация Майкрософт
ms.date: 04/27/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Thread.Name property
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c0c4d74a-0314-4b71-81c9-b0b019347ab8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d0954ffadd1bb1b09d7294be673f961ca2f18058
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62906460"
---
# <a name="how-to-set-a-thread-name-in-managed-code"></a>Практическое руководство. установку имени потока в управляемом коде
Именование потоков можно выполнить в любом выпуске Visual Studio. Именование потоков позволяет отслеживать их в окне **Потоки**.

 Чтобы задать имя потока в управляемом коде, используйте свойство <xref:System.Threading.Thread.Name%2A>.

## <a name="example"></a>Пример

```csharp
public class Needle
{
    // This method will be called when the thread is started.
    public void Baz()
    {
        Console.WriteLine("Needle Baz is running on another thread");
    }
}

public void Main()
{
    Console.WriteLine("Thread Simple Sample");
    Needle oNeedle = new Needle();
    // Create a Thread object.
    System.Threading.Thread oThread = new System.Threading.Thread(oNeedle.Baz);
    // Set the Thread name to "MyThread".
    oThread.Name = "MyThread";
    // Starting the thread invokes the ThreadStart delegate
    oThread.Start();
}
```

```VB
Public Class Needle
    ' This method will be called when the thread is started.
    Sub Baz()
        Console.WriteLine("Needle Baz is running on another thread")
    End Sub
End Class

Sub Main()
    Console.WriteLine("Thread Simple Sample")
    Dim oNeedle As New Needle()
   ' Create a Thread object.
    Dim oThread As New System.Threading.Thread(AddressOf oNeedle.Baz)
    ' Set the Thread name to "MyThread".
    oThread.Name = "MyThread"
    ' Starting the thread invokes the ThreadStart delegate
    oThread.Start()
End Sub
```

## <a name="see-also"></a>См. также
- [Отладка многопоточных приложений](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Практическое руководство. Установка имен потока в машинном коде](../debugger/how-to-set-a-thread-name-in-native-code.md)