---
title: Как тестировать и отлаживать визуализатор | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, testing
- visualizers, debugging
- debugging [Visual Studio], visualizers
ms.assetid: 5cc12ce8-c819-48e4-b487-98d403001b28
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a0d2fdcd0685b83f63e9354b96146c1c869b355
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732396"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Практическое руководство. Тестирование и отладка визуализатора
После написания визуализатора необходимо выполнить отладку и протестировать его.

Одним из способов проверки визуализатора является установка его в Visual Studio и вызов из окна отладчика. (См. раздел [как установить визуализатор](../debugger/how-to-install-a-visualizer.md).) В этом случае необходимо использовать второй экземпляр Visual Studio для присоединения и отладки визуализатора, который выполняется в первом экземпляре отладчика.

Более простой способ отладки визуализатора — запуск визуализатора из тестового драйвера. API визуализатора позволяет легко создать такой драйвер, который называется *узлом разработки визуализатора*.

### <a name="to-create-a-visualizer-development-host"></a>Чтобы создать узел разработки визуализатора

1. В класс отладчика следует включить статический метод, который создает объект <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> и вызывает его метод показа.

    ```csharp
    public static void TestShowVisualizer(object objectToVisualize)
    {
        VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
        myHost.ShowVisualizer();
    }
    ```

    Параметры, используемые для создания узлов, это объект данных, который будет показан в визуализаторе (`objectToVisualize`) и тип класса отладчика.

2. Добавьте следующий оператор для вызова `TestShowVisualizer`. Если визуализатор был создан в библиотеке классов, необходимо создать исполняемый файл для вызова библиотеки классов и поместить в него этот оператор:

    ```csharp
    DebuggerSide.TestShowVisualizer(myString);
    ```

    Более полный пример см. в разделе [Пошаговое руководство. Написание C#визуализатора в ](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).

## <a name="see-also"></a>См. также
- [Пошаговое руководство. Написание визуализатора на C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Практическое руководство. Установка визуализатора](../debugger/how-to-install-a-visualizer.md)
- [Создание настраиваемых визуализаторов](../debugger/create-custom-visualizers-of-data.md)
