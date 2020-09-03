---
title: Пошаговое руководство. Использование интерфейсов API профилировщика | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d5fc0f5a11d29fdb1ee570dc32066fdd492ed8db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68871541"
---
# <a name="walkthrough-using-profiler-apis"></a>Пошаговое руководство. Использование API-интерфейсов профилировщика
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве для демонстрации возможностей интерфейсов API Средств профилирования [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] используется приложение на C#. Интерфейсы API профилировщика используются для ограничения объема данных, собираемых во время профилирования с инструментированием.

 В целом, действия, описанные в этом пошаговом руководстве, можно применять к приложениям на C и C++. Для каждого языка программирования необходимо соответствующим образом настроить среду сборки.

 Анализ производительности приложения, как правило, начинается с профилирования с выборкой. Если с помощью профилирования с выборкой не удается точно локализовать узкое место, можно воспользоваться профилированием с инструментированием для получения более подробных сведений. Профилирование с инструментированием особенно полезно при изучении взаимодействия потоков.

 Однако более высокий уровень детализации приводит к увеличению объема собираемых данных. Порой при профилировании с инструментированием создаются файлы данных очень большого размера. Кроме того, более высока вероятность того, что инструментирование отрицательно скажется на производительности приложения. Дополнительные сведения см. в разделах [Общие сведения о значениях данных инструментирования](../profiling/understanding-instrumentation-data-values.md) и [Общие сведения о значениях выборочных данных](../profiling/understanding-sampling-data-values.md).

 Профилировщик Visual Studio позволяет ограничить объем собираемых данных. В этом пошаговом руководстве приведен пример ограничения сбора данных с помощью интерфейсов API профилировщика. Профилировщик Visual Studio предоставляет интерфейс API для управления сбором данных из приложения.

 Для машинного кода интерфейсы API профилировщика Visual Studio находятся в файле VSPerf.dll. Файл заголовка VSPerf.h и библиотека импорта VSPerf.lib расположены в каталоге Microsoft Visual Studio 9\Team Tools\Performance Tools.

 Для управляемого кода интерфейсы API находятся в файле Microsoft.VisualStudio.Profiler.dll. Эта библиотека DLL расположена в каталоге Microsoft Visual Studio 9\Team Tools\Performance Tools. Дополнительные сведения см. в статье о [пространстве имен Microsoft.VisualStudio.Profiler](/previous-versions/ms242704(v=vs.140)).

## <a name="prerequisites"></a>Предварительные требования
 В этом пошаговом руководстве предполагается, что используемая среда разработки настроена для отладки и выборки. В следующих разделах представлены общие сведения о предварительных требованиях:

 [Как выбрать методы сбора](../profiling/how-to-choose-collection-methods.md)

 [Инструкции: справочные сведения о символах Windows](../profiling/how-to-reference-windows-symbol-information.md)

 По умолчанию при запуске профилировщика он выполняет сбор данных на глобальном уровне. При включении в начало программы указанного ниже кода профилирование на глобальном уровне отключается.

```
DataCollection.StopProfile(
ProfileLevel.Global,
DataCollection.CurrentId);
```

 Сбор данных можно отключить из командной строки, не вызывая интерфейс API. В следующих шагах предполагается, что среда сборки из командной строки настроена для работы как средств профилирования, так и средств разработки. В том числе настроены параметры, необходимые для работы средств VSInstr и VSPerfCmd. См. раздел "Средства профилирования из командной строки".

## <a name="limiting-data-collection-using-profiler-apis"></a>Ограничение сбора данных с помощью интерфейсов API профилировщика

#### <a name="to-create-the-code-to-profile"></a>Создание кода для профилирования

1. Создайте проект C# в Visual Studio или используйте сборку из командной строки в зависимости от ваших предпочтений.

    > [!NOTE]
    > При сборке должна использоваться библиотека Microsoft.VisualStudio.Profiler.dll, расположенная в каталоге Microsoft Visual Studio 9\Team Tools\Performance Tools.

2. Скопируйте и вставьте в проект следующий код:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;
    using Microsoft.VisualStudio.Profiler;

    namespace ConsoleApplication2
    {
        class Program
        {
            public class A
            {
             private int _x;

             public A(int x)
             {
              _x = x;
             }

             public int DoNotProfileThis()
             {
              return _x * _x;
             }

             public int OnlyProfileThis()
             {
              return _x + _x;
             }

             public static void Main()
             {
            DataCollection.StopProfile(
            ProfileLevel.Global,
            DataCollection.CurrentId);
              A a;
              a = new A(2);
              int x;
              Console.WriteLine("2 square is {0}", a.DoNotProfileThis());
              DataCollection.StartProfile(
                  ProfileLevel.Global,
                  DataCollection.CurrentId);
              x = a.OnlyProfileThis();
              DataCollection.StopProfile(
                  ProfileLevel.Global,
                  DataCollection.CurrentId);
              Console.WriteLine("2 doubled is {0}", x);
             }
            }

        }
    }
    ```

#### <a name="to-collect-and-view-data-in-the-visual-studio-ide"></a>Сбор и просмотр данных в интегрированной среде разработки Visual Studio

1. Откройте интегрированную среду разработки [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. В меню **Анализ** наведите указатель мыши на пункт **Профилировщик** и щелкните **Новый сеанс производительности**.

2. Добавьте скомпилированный двоичный файл в список **Целевые объекты** в окне **Обозреватель производительности**. Щелкните правой кнопкой мыши узел **Целевые объекты** и выберите команду **Добавить конечный двоичный файл**. Укажите местоположение двоичного файла в диалоговом окне **Добавление целевого двоичного файла** и нажмите кнопку **Открыть**.

3. На панели инструментов **Обозреватель производительности** в списке **Метод** выберите пункт **Инструментирование**.

4. Нажмите кнопку **Запустить с профилированием**.

    Профилировщик выполнит инструментирование, запустит двоичный файл и создаст файл отчета о производительности. Файл отчета о производительности отображается в узле **Отчеты****обозревателя производительности**.

5. Откройте созданный файл отчета о производительности.

   По умолчанию при запуске профилировщика он выполняет сбор данных на глобальном уровне. При включении в начало программы указанного ниже кода профилирование на глобальном уровне отключается.

```
DataCollection.StopProfile(
ProfileLevel.Global,
DataCollection.CurrentId);
```

#### <a name="to-collect-and-view-data-at-the-command-line"></a>Сбор и просмотр данных из командной строки

1. Скомпилируйте отладочную версию примера кода, созданного ранее в процедуре "Создание кода для профилирования" этого пошагового руководства.

2. В случае профилирования управляемого приложения установите соответствующие переменные среды с помощью следующей команды:

     **VsPefCLREnv /traceon**

3. Введите следующую команду:**VSInstr \<filename> . exe**

4. Введите следующую команду:**VSPerfCmd/start: Trace/OUTPUT: \<filename> . vsp**

5. Введите следующую команду: **VSPerfCmd /globaloff**

6. Выполните программу.

7. Введите следующую команду: **VSPerfCmd /shutdown**

8. Введите следующую команду:**VSPerfReport/calltrace: \<filename> . vsp**

     В текущем каталоге создается CSV-файл, содержащий результирующие данные производительности.

## <a name="see-also"></a>См. также раздел

- [Profiler](/previous-versions/ms242704(v=vs.140))
- [Справочник по API профилировщика Visual Studio (native)](../profiling/visual-studio-profiler-api-reference-native.md)
- [Начало работы](../profiling/getting-started-with-performance-tools.md)
- [Профилирование из командной строки](../profiling/using-the-profiling-tools-from-the-command-line.md)