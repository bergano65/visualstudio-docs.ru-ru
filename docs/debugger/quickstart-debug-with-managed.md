---
title: "Отладка с использованием управляемого кода, с помощью отладчика Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 12/06/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: quickstart
helpviewer_keywords: debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: aa992c0cdcf5c50208aacc8e16d954f4ee35da13
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="debug-with-managed-code-using-the-visual-studio-debugger"></a>Отладка с использованием управляемого кода, с помощью отладчика Visual Studio

Отладчик Visual Studio предоставляет множество мощные средства для отладки приложений. В этом разделе предоставляет быстрый способ узнать некоторые основные возможности.

## <a name="create-a-new-project"></a>Создание нового проекта 

1. В Visual Studio выберите **файл > Новый проект**.

2. В разделе **Visual C#** или **Visual Basic**, выберите **.NET Core**, а затем в средней области выберите **консольного приложения (.NET Core)**.

     Если шаблон проекта **Консольное приложение (.NET Core)** отсутствует, выберите ссылку **Открыть Visual Studio Installer** в левой области диалогового окна **Новый проект**. Запускается Visual Studio Installer. Выберите **разработки настольных приложений .NET** и **.NET Core** рабочей нагрузки, нажмите кнопку **изменить**.

3. Введите имя, например **MyDbgApp** и нажмите кнопку **ОК**.

    Visual Studio создаст проект.

4. Замените следующий код в Program.cs или Module1.vb,

    ```c#
    class Program
    {
        static void Main(string[] args)
        {
        }
    }
    ```

    ```vb
    Module Module1
        Sub Main()
        End Sub
    End Module
    ```

    следующим кодом:

    ```c#
    class Program
    {
        private static void doWork()
        {
            LinkedList<int> c1 = new LinkedList<int>();

            c1.AddLast(10);
            c1.AddLast(20);

            LinkedList<int> c2 = new LinkedList<int>(c1);
            int i = c2.First.Value;
            int j = c2.First.Value;
            Console.Write("The first element is ");
            Console.Write(i);
            Console.Write("\n");
            Console.Write("The second element is ");
            Console.Write(j);
            Console.Write("\n");

        }

        static int Main()
        {
            // using namespace std;
            doWork();
            return 0;

        }
    }
    ```

    ```vb
    Imports System.Collections.Generic

    Namespace MyDbgApp
        Class Program
            Private Shared Sub doWork()
                Dim c1 As New LinkedList(Of Integer)()

                c1.AddLast(10)
                c1.AddLast(20)

                Dim c2 As New LinkedList(Of Integer)(c1)
                Dim i As Integer = c2.First.Value
                Dim j As Integer = c2.First.Value
                Console.Write("The first element is ")
                Console.Write(i)
                Console.Write(vbLf)
                Console.Write("The second element is ")
                Console.Write(j)
                Console.Write(vbLf)

            End Sub

            Public Shared Function Main() As Integer
                ' using namespace std;
                doWork()
                Return 0

            End Function
        End Class
    End Namespace
    ```

    > [!NOTE]
    > В Visual Basic убедитесь, что автоматически запускаемый объект имеет значение `Sub Main` (**свойства > приложения > автоматически запускаемый объект**).

## <a name="set-a-breakpoint"></a>Задание точки останова

Объект *останова* является маркер, указывающий, где Visual Studio следует приостановить ваш выполнение кода, чтобы вы могли проверить значения переменных или поведение памяти или ли начало выполнения ветви кода. Это самый простой компонент отладки.

1. Чтобы задать точку останова, щелкните в области слева от `doWork` вызов функции (или выберите строку кода и нажмите клавишу **F9**).

    ![Установите точку останова](../debugger/media/dbg-qs-set-breakpoint-csharp.png "установить точку останова")

2. Теперь нажмите клавишу **F5** (или выберите **Отладка > Начать отладку**).

    ![Точки останова,](../debugger/media/dbg-qs-hit-breakpoint-csharp.png "точки останова")

    Отладчик приостанавливает, где вы задали точку останова. Инструкция приостановки выполнения отладчика и приложения обозначается желтой стрелкой. В строке с `doWork` вызов функции еще не выполнен.

    > [!TIP]
    > При наличии точки останова в цикле или рекурсии или если у вас много точек останова, которые часто пошаговом выполнении, используйте [условную точку останова](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) чтобы убедиться в том, что кода приостанавливается только в том случае, если соблюдаются определенные условия. Это экономит время и может упростить для отладки проблем, которые трудно воспроизвести.

## <a name="navigate-code"></a>Навигация по коду

Существуют различные команды, чтобы отладчик, чтобы продолжить. Мы рассмотрим команду навигации полезный код, новые возможности Visual Studio 2017 г.

- Пока выполнение приостановлено в точке останова, наведите указатель мыши на инструкцию `c1.AddLast(20)` до зеленая **выполнения щелкните** кнопку ![запуска щелкните](../debugger/media/dbg-tour-run-to-click.png "RunToClick") и нажмите клавишу **Выполнения щелкните** кнопки.

    ![Запуск щелкнуть](../debugger/media/dbg-qs-run-to-click-csharp.png "выполнения нажмите кнопку")

    Приложение продолжает выполнение, вызвав `doWork`и останавливается на строке кода, где была нажата кнопка.

    Общие команды клавиатуры для включения пошагового выполнения кода **F10** и **F11**. Более подробные инструкции см. в разделе [руководство для начинающих](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Отслеживание значений переменных в подсказке по данным

1. В текущей строке кода (отмечено указатель выполнения желтый), наведите указатель мыши `c1` объекта с помощью мыши для отображения подсказки данных.

    ![Просмотреть подсказку](../debugger/media/dbg-qs-data-tip-csharp.png "просмотра подсказки данных")

    Подсказка отображается текущее значение `c1` переменной и позволяет проверять его свойства. При отладке, если значение, которое не нужны, возможно, имеется ошибка в предыдущей или вызывающей строке кода. 

2. Разверните подсказка для просмотра текущего значения свойства `c1` объекта.

3. Чтобы прикрепить подсказку данных, чтобы его можно просмотреть значение `c1` при выполнении кода, щелкните значок небольших ПИН-код. (Закрепленная подсказка данных будет можно переместить в удобном расположении.)

## <a name="edit-code-and-continue-debugging"></a>Изменить код и продолжить отладку

Если обнаруживается изменение, которое необходимо проверить в коде в середине сеанса отладки, это можно сделать, слишком.

1. Щелкните второй экземпляр `c2.First.Value` и измените `c2.First.Value` для `c2.Last.Value`.

2. Нажмите клавишу **F10** (или **Отладка > шаг с обходом**) несколько раз, чтобы переместить отладчик и выполнять отредактированным кодом.

    ![Изменить и продолжить](../debugger/media/dbg-qs-edit-and-continue-csharp.gif "изменить и продолжить")

    **F10** перемещает оператор отладчика один раз, но действия над функциями вместо обработки изнутри их (код, который можно пропустить все еще выполняет).

Дополнительные сведения об использовании edit and continue и ограничениях см. [изменить и продолжить](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Следующие шаги

- Дополнительные сведения об отладчике см. в разделе [запустить отладчик и перемещаться по коду](../debugger/getting-started-with-the-debugger.md).
- Чтобы узнать больше о точках останова, в разделе [использование точек останова](../debugger/using-breakpoints.md).

## <a name="see-also"></a>См. также  
 [Отладка в Visual Studio](../debugger/index.md)  
 [Обзор функций отладчика](../debugger/debugger-feature-tour.md)
