---
title: Практическое руководство. Тестирование и отладка визуализатора | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- visualizers, testing
- visualizers, debugging
- debugging [Visual Studio], visualizers
ms.assetid: 5cc12ce8-c819-48e4-b487-98d403001b28
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 18261d9e8c6c7d3f65dea7c72439b29f4e2e0df3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68176495"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Практическое руководство. тестирование и отладку визуализатора
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

После написания визуализатора необходимо выполнить отладку и протестировать его.  
  
 Одним из способов проверки визуализатора является установка его в Visual Studio и вызов из окна отладчика. (См. [Практическое руководство. Установка визуализатора](../debugger/how-to-install-a-visualizer.md).) При этом понадобится второй экземпляр Visual Studio для присоединения к визуализатору, запущенному на первом отладчике, и его отладки.  
  
 Более простой способ отладки визуализатора — запуск визуализатора из тестового драйвера. API визуализатора позволяет легко создать такой драйвер, который называется *узлом разработки визуализатора*.  
  
### <a name="to-create-a-visualizer-development-host"></a>Чтобы создать узел разработки визуализатора  
  
1. В класс отладчика следует включить статический метод, который создает объект <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> и вызывает его метод показа.  
  
    ```  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       myHost.ShowVisualizer();  
    }  
    ```  
  
     Параметры, используемые для создания узлов, это объект данных, который будет показан в визуализаторе (`objectToVisualize`) и тип класса отладчика.  
  
2. Добавьте следующий оператор для вызова `TestShowVisualizer`. Если визуализатор был создан в библиотеке классов, необходимо создать исполняемый файл для вызова библиотеки классов и поместить в него этот оператор:  
  
    ```  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
     Более полный пример, см. в разделе [Пошаговое руководство: Написание визуализатора на C# ](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: написание визуализатора на C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [Практическое руководство. Установка визуализатора](../debugger/how-to-install-a-visualizer.md)   
 [Создание настраиваемых визуализаторов](../debugger/create-custom-visualizers-of-data.md)
