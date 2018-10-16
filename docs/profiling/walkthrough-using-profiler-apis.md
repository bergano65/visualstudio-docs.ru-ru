---
title: Пошаговое руководство. Использование интерфейсов API профилировщика | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a6c6d4a5fce3bbd3d050d3aaae4908b59d745596
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468214"
---
# <a name="walkthrough-using-profiler-apis"></a>Пошаговое руководство. Использование API-интерфейсов профилировщика

В этом пошаговом руководстве для демонстрации возможностей интерфейсов API Средств профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] используется приложение на C#. Интерфейсы API профилировщика используются для ограничения объема данных, собираемых во время профилирования с инструментированием.  
  
 В целом, действия, описанные в этом пошаговом руководстве, можно применять к приложениям на C и C++. Для каждого языка программирования необходимо соответствующим образом настроить среду сборки.  
  
 Анализ производительности приложения, как правило, начинается с профилирования с выборкой. Если с помощью профилирования с выборкой не удается точно локализовать узкое место, можно воспользоваться профилированием с инструментированием для получения более подробных сведений. Профилирование с инструментированием особенно полезно при изучении взаимодействия потоков.  
  
 Однако более высокий уровень детализации приводит к увеличению объема собираемых данных. Порой при профилировании с инструментированием создаются файлы данных очень большого размера. Кроме того, более высока вероятность того, что инструментирование отрицательно скажется на производительности приложения. Дополнительные сведения см. в статьях [Общие сведения о значениях данных инструментирования в средствах профилирования](../profiling/understanding-instrumentation-data-values.md) и [Общие сведения о значениях выборочных данных](../profiling/understanding-sampling-data-values.md).  
  
 Профилировщик Visual Studio позволяет ограничить объем собираемых данных. В этом пошаговом руководстве приведен пример ограничения сбора данных с помощью интерфейсов API профилировщика. Профилировщик Visual Studio предоставляет интерфейс API для управления сбором данных из приложения.  
  
 Для машинного кода интерфейсы API профилировщика Visual Studio находятся в файле *VSPerf.dll*. Файл заголовка *VSPerf.h* и библиотека импорта *VSPerf.lib* расположены в каталоге *Microsoft Visual Studio 9\Team Tools\Performance Tools*.  
  
 Для управляемого кода интерфейсы API находятся в файле *Microsoft.VisualStudio.Profiler.dll*. Эта библиотека DLL расположена в каталоге *Microsoft Visual Studio 9\Team Tools\Performance Tools*. Дополнительные сведения см. в разделе <xref:Microsoft.VisualStudio.Profiler>.  
  
## <a name="prerequisites"></a>Предварительные требования  
 В этом пошаговом руководстве предполагается, что используемая среда разработки настроена для отладки и выборки. В следующих разделах представлены общие сведения о предварительных требованиях:  
  
 [Практическое руководство. Выбор методов сбора данных](../profiling/how-to-choose-collection-methods.md)  
  
 [Практическое руководство. Справочная информация о символах Windows](../profiling/how-to-reference-windows-symbol-information.md)  
  
 По умолчанию при запуске профилировщика он выполняет сбор данных на глобальном уровне. При включении в начало программы указанного ниже кода профилирование на глобальном уровне отключается.  
  
```csharp  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
 Сбор данных можно отключить из командной строки, не вызывая API. В следующих шагах предполагается, что среда сборки из командной строки настроена для работы как средств профилирования, так и средств разработки. В том числе настроены параметры, необходимые для работы средств VSInstr и VSPerfCmd. См. дополнительные сведения о [средствах профилирования командной строки](../profiling/using-the-profiling-tools-from-the-command-line.md).  
  
## <a name="limit-data-collection-using-profiler-apis"></a>Ограничение сбора данных с помощью интерфейсов API профилировщика  
  
#### <a name="to-create-the-code-to-profile"></a>Создание кода для профилирования  
  
1.  Создайте проект C# в Visual Studio или используйте сборку из командной строки в зависимости от ваших предпочтений.  
  
    > [!NOTE]
    >  При сборке должна использоваться библиотека *Microsoft.VisualStudio.Profiler.dll*, расположенная в каталоге *Microsoft Visual Studio 9\Team Tools\Performance Tools*.  
  
2.  Скопируйте и вставьте в проект следующий код:  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using Microsoft.VisualStudio.Profiler;  
  
    namespace ConsoleApplication1  
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

                    A a = new A(2);  
                    Console.WriteLine("2 square is {0}", a.DoNotProfileThis()); 

                    DataCollection.StartProfile(  
                    ProfileLevel.Global,  
                    DataCollection.CurrentId);

                    int x;  
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
  
1.  Откройте интегрированную среду разработки [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. В меню **Анализ** наведите указатель мыши на пункт **Профилировщик** и щелкните **Новый сеанс производительности**.  
  
2.  Добавьте скомпилированный двоичный файл в список **Целевые объекты** в окне **Обозреватель производительности**. Щелкните правой кнопкой мыши узел **Целевые объекты** и выберите команду **Добавить конечный двоичный файл**. Укажите местоположение двоичного файла в диалоговом окне **Добавление целевого двоичного файла** и нажмите кнопку **Открыть**.  
  
3.  На панели инструментов **Обозреватель производительности** в списке **Метод** выберите пункт **Инструментирование**.  
  
4.  Нажмите кнопку **Запустить с профилированием**.  
  
     Профилировщик выполнит инструментирование, запустит двоичный файл и создаст файл отчета о производительности. Файл отчета о производительности отображается в узле **Отчеты** **обозревателя производительности**.  
  
5.  Откройте созданный файл отчета о производительности.  
  
 По умолчанию при запуске профилировщика он выполняет сбор данных на глобальном уровне. При включении в начало программы указанного ниже кода профилирование на глобальном уровне отключается.  
  
```csharp  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
#### <a name="to-collect-and-view-data-at-the-command-line"></a>Сбор и просмотр данных из командной строки  
  
1.  Скомпилируйте отладочную версию примера кода, созданного ранее в процедуре "Создание кода для профилирования" этого пошагового руководства.  
  
2.  В случае профилирования управляемого приложения установите соответствующие переменные среды с помощью следующей команды:  
  
     **VsPerfCLREnv /traceon**.  
  
3.  Введите следующую команду: **VSInstr \<имя_файла>.exe**.  
  
4.  Введите следующую команду: **VSPerfCmd /start:trace /output:\<имя_файла>.vsp**.  
  
5.  Введите следующую команду: **VSPerfCmd /globaloff**.  
  
6.  Выполните программу.  
  
7.  Введите следующую команду: **VSPerfCmd /shutdown**.  
  
8.  Введите следующую команду: **VSPerfReport /calltrace:\<имя_файла>.vsp**.  
  
     В текущем каталоге создается *CSV*-файл, содержащий результирующие данные производительности.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Profiler>   
 [Справочник по API-интерфейсам профилировщика Visual Studio (машинный код)](../profiling/visual-studio-profiler-api-reference-native.md)   
 [Приступая к работе со средствами профилирования](../profiling/getting-started-with-performance-tools.md)   
 [Профилирование из командной строки](../profiling/using-the-profiling-tools-from-the-command-line.md)
