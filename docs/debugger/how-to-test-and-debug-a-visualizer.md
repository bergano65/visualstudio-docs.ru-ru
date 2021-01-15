---
title: Тестирование и отладка визуализатора | Документация Майкрософт
description: Тестирование и отладка визуализатора путем его запуска из тестового драйвера (узел разработки визуализатора) или установки в Visual Studio с последующим вызовом из окна отладчика.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 1326fe9731a9d938678eb9397b106ab9e71b4fd5
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150669"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Практическое руководство. тестирование и отладку визуализатора
После написания визуализатора необходимо выполнить отладку и протестировать его.

Одним из способов проверки визуализатора является установка его в Visual Studio и вызов из окна отладчика. (См. [Практическое руководство. Установка визуализатора](../debugger/how-to-install-a-visualizer.md).) При этом понадобится второй экземпляр Visual Studio для присоединения к визуализатору, запущенному на первом отладчике, и его отладки.

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

    Более полный пример см. в разделе [Практическое руководство. Написание визуализатора на C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).

## <a name="see-also"></a>См. также
- [Пошаговое руководство: Написание визуализатора на C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Практическое руководство. Установка визуализатора](../debugger/how-to-install-a-visualizer.md)
- [Создание настраиваемых визуализаторов](../debugger/create-custom-visualizers-of-data.md)
