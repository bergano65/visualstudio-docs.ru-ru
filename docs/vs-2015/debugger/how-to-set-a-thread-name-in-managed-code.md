---
title: 'Практическое: Установка имени потока в управляемом коде | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Thread.Name property
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c0c4d74a-0314-4b71-81c9-b0b019347ab8
caps.latest.revision: 31
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0175bee3280f3ecfdb49fc280007810d4e1c2860
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570359"
---
# <a name="how-to-set-a-thread-name-in-managed-code"></a>Практическое руководство. Установка имени потока в управляемом коде
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: Установка имени потока в управляемом коде](https://docs.microsoft.com/visualstudio/debugger/how-to-set-a-thread-name-in-managed-code).  
  
Именование потоков можно выполнить в любом выпуске Visual Studio. Именование потоков полезно для отслеживания потоков в **потоков** окна. Так как **потоков** окно будет недоступно в выпусках Visual Studio Express, именование потоков не имеет практического смысла в выпусках Express.  
  
 Чтобы задать имя потока в управляемом коде, используйте свойство <xref:System.Threading.Thread.Name%2A>.  
  
## <a name="example"></a>Пример  
  
```  
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
    ' Set the Thread name to "MainThread".  
    oThread.Name = "MainThread"  
    ' Starting the thread invokes the ThreadStart delegate  
    oThread.Start()  
End Sub  
```  
  
## <a name="see-also"></a>См. также  
 [Отладка многопоточных приложений](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Практическое руководство. Установка имен потока в машинном коде](../debugger/how-to-set-a-thread-name-in-native-code.md)



