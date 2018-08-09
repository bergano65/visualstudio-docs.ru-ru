---
title: Отладка управляемого кода | Документация Майкрософт
description: Отладка C# или Visual Basic с помощью отладчика Visual Studio
ms.custom: mvc
ms.date: 03/18/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 2ba06156a8fa44a61b489deba6104673e8fb08ce
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637527"
---
# <a name="quickstart-debug-with-managed-code-using-the-visual-studio-debugger"></a>Краткое руководство: Отладка с помощью управляемого кода, с помощью отладчика Visual Studio

Отладчик Visual Studio предоставляет множество эффективных возможностей для отладки приложений. В этой статье вы ознакомитесь с некоторыми основными возможностями.

## <a name="create-a-new-project"></a>Создание нового проекта 

1. В Visual Studio последовательно выберите **Файл > Создать проект**.

2. В разделе **Visual C#** или **Visual Basic**, выберите **.NET Core**, а затем в средней области выберите **консольное приложение (.NET Core)**.

     Если шаблон проекта **Консольное приложение (.NET Core)** отсутствует, выберите ссылку **Открыть Visual Studio Installer** в левой области диалогового окна **Новый проект**. Запускается Visual Studio Installer. Выберите **разработка классических приложений .NET** и **.NET Core** рабочей нагрузки, затем выберите **изменить**.

3. Введите имя, например **MyDbgApp** и нажмите кнопку **ОК**.

    Visual Studio создаст проект.

4. В *Program.cs* или *Module1.vb*, замените код

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

## <a name="set-a-breakpoint"></a>Задание точки останова

Объект *точки останова* является маркер, указывающий, где Visual Studio следует приостановить открытом кода, поэтому вы можете взгляните на значения переменных или поведение памяти или ли начало выполнения ветви кода. Это основная функция при отладке.

1. Чтобы задать точку останова, щелкните в области слева от `doWork` вызов функции (или выберите строку кода и нажмите клавишу **F9**).

    ![Установите точку останова](../debugger/media/dbg-qs-set-breakpoint-csharp.png "установите точку останова")

2. Теперь нажмите клавишу **F5** (или выберите **Отладка > Начать отладку**).

    ![Точки останова,](../debugger/media/dbg-qs-hit-breakpoint-csharp.png "точки останова")

    Отладчик приостанавливает, где вы задали точку останова. Инструкции, где приостановлено выполнение отладчик и приложение обозначается желтой стрелкой. Строка с `doWork` вызов функции еще не выполнена.

    > [!TIP]
    > Если вы установили точку останова в цикле или рекурсии или если у вас есть много точек останова, которые вы часто пошагово, [условную точку останова](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) чтобы убедиться в том, что позволяет приостанавливать код только в том случае, если соблюдаются определенные условия. Условную точку останова можно сэкономить время, и его можно также упростить его для отладки проблем, которые трудно воспроизвести.

## <a name="navigate-code"></a>Навигация по коду

Существуют разные команды, чтобы отладчика для возобновления выполнения. Мы покажем команды перехода полезный код, который впервые появился в Visual Studio 2017.

Пока выполнение приостановлено в точке останова, наведите указатель мыши инструкцию `c1.AddLast(20)` до зеленую **выполнение до щелкнутого** кнопку ![выполнение до щелкнутого](../debugger/media/dbg-tour-run-to-click.png "RunToClick") и нажмите клавишу **Выполнение до щелкнутого** кнопки.

![Выполнение до щелкнутого](../debugger/media/dbg-qs-run-to-click-csharp.png "выполнение до щелкнутого")

Приложение продолжает выполнение, вызвав `doWork`, а приостанавливается на строке кода, где была нажата кнопка.

Общие команды клавиатуры, используемый для пошагового выполнения кода включают **F10** и **F11**. Более подробные инструкции см. в разделе [руководство для начинающих](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Проверить значения переменных в подсказке по данным

1. В текущей строке кода (обозначен указатель желтый выполнения), наведите указатель мыши `c1` объекта с помощью мыши для отображения подсказки данных.

    ![Просмотреть подсказку](../debugger/media/dbg-qs-data-tip-csharp.png "просматривать подсказки данных")

    Подсказка показывает текущее значение `c1` переменной и позволяет просмотреть его свойства. При отладке, если вы видите значение, которое вряд ли будет возможно имеется ошибка в предыдущей или вызывающей строке кода. 

2. Разверните подсказки данных, чтобы просмотреть текущие значения свойств `c1` объекта.

3. Чтобы прикрепить подсказку данных, таким образом, вы можете увидеть значение `c1` при выполнении кода, щелкните значок небольших ПИН-код. (Закрепленная подсказка данных будет можно переместить в удобном расположении.)

## <a name="edit-code-and-continue-debugging"></a>Изменение кода и продолжение отладки

Если обнаруживается изменение, которое вы хотите протестировать в коде в ходе сеанса отладки, это можно сделать, слишком.

1. Щелкните второй экземпляр `c2.First.Value` и измените `c2.First.Value` для `c2.Last.Value`.

2. Нажмите клавишу **F10** (или **Отладка > шаг с обходом**) несколько раз, чтобы переместить отладчик и выполнить измененный код.

    ![Изменить и продолжить](../debugger/media/dbg-qs-edit-and-continue-csharp.gif "изменить и продолжить")

    **F10** перемещает отладчиком по одному оператору во время, но действия функции вместо шаг с заходом в их (код, который вы пропускаете по-прежнему выполняется).

Дополнительные сведения об использовании изменить и продолжить и ограничениях см. в разделе [изменить и продолжить](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Следующие шаги

В этом руководстве вы узнали, как запустить отладчик, пошаговое выполнение кода и проверять значения переменных. Вы можете получить подробный обзор функций отладчика, а также ссылки на дополнительные сведения.

> [!div class="nextstepaction"]
> [Обзор функций отладчика](../debugger/debugger-feature-tour.md)
