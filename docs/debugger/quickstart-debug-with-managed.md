---
title: Отладка управляемого кода | Документация Майкрософт
description: Отладка C# или Visual Basic с помощью отладчика Visual Studio
ms.custom: mvc
ms.date: 03/18/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8c8616ffc9adeebe5fd2b224366d05cbf5c66a2e
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2019
ms.locfileid: "57525379"
---
# <a name="quickstart-debug-with-c-or-visual-basic-using-the-visual-studio-debugger"></a>Краткое руководство. Отладка с использованием C# или Visual Basic с помощью отладчика Visual Studio

Отладчик Visual Studio реализует множество эффективных функций для отладки приложений. В этой статье вы ознакомитесь с некоторыми основными возможностями.

## <a name="create-a-new-project"></a>Создание нового проекта

1. В Visual Studio последовательно выберите **Файл > Создать проект**.

2. В разделе **Visual C#** или **Visual Basic** выберите **.NET Core**, а затем в средней области выберите **Консольное приложение (.NET Core)**.

     Если шаблон проекта **Консольное приложение (.NET Core)** отсутствует, выберите ссылку **Открыть Visual Studio Installer** в левой области диалогового окна **Новый проект**. Запускается Visual Studio Installer. Выберите рабочую нагрузку **Разработка классических приложений .NET** и **.NET Core** и щелкните **Изменить**.

3. Введите имя, например **MyDbgApp**, и нажмите кнопку **ОК**.

    Visual Studio создаст проект.

4. В *Program.cs* или *Module1.vb* замените код

    ```csharp
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

    ```csharp
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
    > Убедитесь в том, что в Visual Basic задан автоматически запускаемый объект `Sub Main` (**Свойства > Приложение > Автоматически запускаемый объект**).

## <a name="set-a-breakpoint"></a>Установка точки останова

*Точка останова* указывает, где Visual Studio следует приостановить выполнение кода, чтобы вы могли проверить значения переменных или поведение памяти, либо выполнение ветви кода. Эта возможность чаще всего используется при отладке.

1. Чтобы задать точку останова, щелкните в области слева от вызова функции `doWork` (или выберите строку кода и нажмите клавишу **F9**).

    ![Задание точки останова](../debugger/media/dbg-qs-set-breakpoint-csharp.png "Задание точки останова")

2. Нажмите клавишу **F5** (или выберите **Отладка > Начать отладку**).

    ![Попадание в точку останова](../debugger/media/dbg-qs-hit-breakpoint-csharp.png "Попадание в точку останова")

    Отладчик приостановит выполнение в заданной точке останова. Инструкция, в которой отладчик приостановил выполнение приложения, обозначается желтой стрелкой. Строка, содержащая вызов функции `doWork`, пока еще не выполнена.

    > [!TIP]
    > При наличии точки останова в цикле или рекурсии либо большого числа точек останова, которые вы часто будете просматривать пошагово, используйте [условную точку останова](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression), которая позволяет приостанавливать код только при выполнении определенных условий. Использование условных точек останова позволяет сэкономить время и упростить отладку проблем, которые сложно воспроизвести.

## <a name="navigate-code"></a>Навигация по коду

Чтобы продолжить работу отладчика, можно использовать различные команды. Здесь описываются полезные новые команды для навигации по коду, доступные с версии Visual Studio 2017.

Если выполнение приостановлено в точке останова, наведите указатель мыши на инструкцию `c1.AddLast(20)` и дождитесь, пока появится зеленая кнопка **Выполнение до щелкнутого** ![Выполнение до щелкнутого](../debugger/media/dbg-tour-run-to-click.png "RunToClick"), после чего нажмите кнопку **Выполнение до щелкнутого**.

![Выполнение до щелкнутого](../debugger/media/dbg-qs-run-to-click-csharp.png "Выполнение до щелкнутого")

Выполнение приложения продолжится путем вызова `doWork` и будет приостановлено в той строке, в которой вы нажмете эту кнопку.

В процессе пошагового выполнения кода обычно используются клавиши **F10** и **F11**. Более подробные инструкции см. в статье [Знакомство с отладчиком Visual Studio](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-datatip"></a>Проверка переменных в подсказке по данным

1. В текущей строке кода, отмеченной желтым указателем выполнения, наведите указатель мыши на объект `c1`, чтобы просмотреть подсказку по данным.

    ![Просмотр подсказки по данным](../debugger/media/dbg-qs-data-tip-csharp.png "Просмотр подсказки по данным")

    Подсказка по данным содержит текущее значение переменной `c1` и позволяет проверить ее свойства. Если во время отладки отображается значение, которое вы не ожидали увидеть, возможно, в предыдущей или вызывающей строке кода имеется ошибка.

2. Разверните подсказку по данным, чтобы просмотреть текущие значения свойств объекта `c1`.

3. Чтобы закрепить подсказку по данным и иметь возможность постоянно просматривать значение переменной `c1` во время выполнения, щелкните небольшой значок булавки. (При необходимости вы можете переместить закрепленную подсказку по данным в удобное положение.)

## <a name="edit-code-and-continue-debugging"></a>Изменение кода и продолжение отладки

Вы можете сделать это во время сеанса отладки, если вам потребуется внести изменения в код.

1. Щелкните второй экземпляр `c2.First.Value` и измените `c2.First.Value` на `c2.Last.Value`.

2. Нажмите клавишу **F10** (или выберите команду **Отладка > Шаг с обходом**) несколько раз, чтобы пройти вперед и выполнить измененный код.

    ![Изменение и продолжение](../debugger/media/dbg-qs-edit-and-continue-csharp.gif "Изменение и продолжение")

    При нажатии клавиши **F10** отладчик каждый раз переходит вперед на одну инструкцию, однако при этом минует функции, не заходя в них (пропускаемый код в таком случае по-прежнему выполняется).

Дополнительные сведения об этом режиме и его ограничениях см. в статье [Изменить и продолжить](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Следующие шаги

В этом руководстве вы узнали, как запускать отладчик, осуществлять пошаговое выполнение кода и проверять переменные. Возможно, вы захотите получить более полное представление о функциях отладчика, а также воспользоваться ссылками на дополнительные сведения.

> [!div class="nextstepaction"]
> [Обзор функций отладчика](../debugger/debugger-feature-tour.md)
