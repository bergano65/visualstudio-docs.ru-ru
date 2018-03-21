---
title: "Модульное тестирование кода Visual C# в Visual Studio | Документация Майкрософт"
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload:
- uwp
author: gewarren
ms.openlocfilehash: 76fc58ff012a813358957ab060b684f8d7e2b5e1
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2018
---
# <a name="unit-testing-visual-c-code"></a>Модульное тестирование кода Visual C#

В этом разделе описывается один из способов создания модульных тестов для класса Visual C# в приложении универсальной платформы Windows. Класс Rooter демонстрирует концепции теории пределов из математического анализа за счет реализации функции, которая вычисляет оценку квадратного корня из заданного числа. Приложение Maths затем может использовать эту функцию для представления интересных операций, которые можно выполнять с помощью математических функций.

В этом разделе демонстрируется использование модульного тестирования в качестве первого шага разработки. При таком подходе сначала необходимо написать метод теста, который проверяет определенное поведение тестируемой системы, а затем написать код, который проходит этот тест. Порядок описанных ниже процедур можно изменить, и сначала написать код, который требуется протестировать, а затем написать сами модульные тесты.

В этом разделе также создается одно решение Visual Studio и отдельные проекты для модульных тестов и для тестируемой библиотеки DLL. Модульные тесты можно включить непосредственно в проект библиотеки DLL или создать отдельные решения для модульных тестов и для DLL.

## <a name="create-the-solution-and-the-unit-test-project"></a>Создание решения и проекта модульного теста

1. В меню **Файл** последовательно выберите пункты **Создать** > **Проект**.

2. В диалоговом окне **Новый проект** разверните узел **Установленные** > **Visual C#** и выберите **Универсальные приложения Windows**. В списке шаблонов проектов выберите **Пустое приложение**.

3. Назовите проект `Maths` и проверьте, что установлен флажок **Создать каталог для решения**.

4. В обозревателе решений выберите имя решения, в контекстном меню выберите команду **Добавить** и выберите пункт **Новый проект**.

5. В диалоговом окне **Новый проект** разверните узел **Установленные**, узел **Visual C#** и выберите **Универсальные приложения**. В списке шаблонов проектов выберите **Приложение модульного тестирования (универсальное приложение Windows)**.

6. В редакторе Visual Studio откройте файл *UnitTest1.cs*.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;
   using Microsoft.VisualStudio.TestTools.UnitTesting;
   using Maths;

   namespace RooterTests
   {
       [TestClass]
       public class UnitTest1

           [TestMethod]
           public void TestMethod1()
           {

           }
   ```

   Обратите внимание на следующее.

   - Каждый тест определен с помощью атрибута <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>. Метод теста должен возвращать значение типа void и не может иметь параметров.

   - Методы теста должны находиться в классе, обозначенном атрибутом <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>.

        При запуске тестов создается экземпляр каждого класса теста. Тестовые методы вызываются в неопределенном порядке.

   - Можно задать особые методы, которые вызываются до и после каждого модуля, класса или метода. Дополнительные сведения см. в статье об использовании [платформы MSTest в модульных тестах](../test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md).

## <a name="verify-that-the-tests-run-in-test-explorer"></a>С помощью обозревателя тестов проверьте, что тесты выполняются

1. Добавьте какой-нибудь тестовый код в TestMethod1 в файле **TestMethod1.cs**:

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   Обратите внимание, что класс <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> содержит несколько статических методов, которые можно использовать для проверки результатов в тестовых методах.

2. В меню **Тест** выберите **Выполнить**, а затем выберите **Запустить все**.

   Будет построен и запущен проект теста. Появится окно обозревателя тестов, а тест будет указан в разделе **Пройденные тесты**. Область сводки в нижней части окна содержит дополнительные сведения о выбранном тесте.

   ![Обозреватель тестов](../test/media/ute_cpp_testexplorer_testmethod1.png)

## <a name="add-the-rooter-class-to-the-maths-project"></a>Добавление класса Rooter в проект Maths

1. В обозревателе решений выберите имя проекта **Maths**. В контекстном меню выберите команду **Добавить** и затем **Класс**.

2. Назовите файл класса *Rooter.cs*.

3. Добавьте следующий код в файл класса Rooter *Rooter.cs*:

   ```csharp
   public Rooter()
   {
   }

   // estimate the square root of a number
   public double SquareRoot(double x)
   {
       return 0.0;
   }
   ```

   Класс `Rooter` объявляет конструктор и метод оценки `SquareRoot`.

4. Метод `SquareRoot` представляет собой минимальную реализацию, достаточную для проверки базовой структуры тестирования.

## <a name="couple-the-test-project-to-the-app-project"></a>Объединение проекта теста с проектом приложения

1. Добавьте ссылку на приложение Maths в проект RooterTests.

    1. В обозревателе решений выберите проект **RooterTests** и в контекстном меню выберите команду **Добавить ссылку**.

    2. В диалоговом окне **Добавить ссылку — RooterTests** разверните узел **Решение** и выберите **Проекты**. Затем выберите элемент **Maths**.

        ![Добавление ссылки на проект Maths](../test/media/ute_cs_windows_addreference.png)

2. Добавьте оператор using в файл *UnitTest1.cs*:

    1. Откройте файл *UnitTest1.cs*.

    2. Добавьте следующий код ниже строки `using Microsoft.VisualStudio.TestTools.UnitTesting;`:

       ```csharp
       using Maths;
       ```

3. Добавьте тест, который использует функцию Rooter. Добавьте следующий код в файл *UnitTest1.cs*:

   ```csharp
   [TestMethod]
   public void BasicTest()
   {
       Maths.Rooter rooter = new Rooter();
       double expected = 0.0;
       double actual = rooter.SquareRoot(expected * expected);
       double tolerance = .001;
       Assert.AreEqual(expected, actual, tolerance);
   }
   ```

4. Постройте решение.

   Новый тест появится в обозревателе тестов в узле **Незапускавшиеся тесты**.

5. В разделе "Обозреватель тестов" выберите **Запустить все**.

   ![Основной тест пройден](../test/media/ute_cpp_testexplorer_basictest.png)

Вы настроили тест и проекты кода и подтвердили, что можно выполнять тесты, которые запускают функции из проекта кода. Теперь можно начать писать реальные тесты и код.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a>Итеративное расширение тестов и обеспечение их успешного выполнения

1. Добавьте новый тест.

   ```csharp
   [TestMethod]
   public void RangeTest()
   {
       Rooter rooter = new Rooter();
       for (double v = 1e-6; v < 1e6; v = v * 3.2)
       {
           double expected = v;
           double actual = rooter.SquareRoot(v*v);
           double tolerance = ToleranceHelper(expected);
           Assert.AreEqual(expected, actual, tolerance);
       }
   }
   ```

   > [!TIP]
   > Рекомендуется не изменять пройденные тесты. Вместо этого добавьте новый тест, обновите код так, чтобы тест проходил успешно, а затем добавьте еще один тест и т. д.
   >
   > При изменении пользователями требований отключите тесты, которые больше не являются корректными. Создайте новые тесты и сделайте так, чтобы они работали по одному в инкрементном режиме.

2. В разделе "Обозреватель тестов" выберите **Запустить все**.

3. Тест не пройден.

   ![Сбой теста RangeTest](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > Непосредственно после написания кода теста проверьте, что тест не пройден. Это поможет избежать распространенной ошибки, заключающейся в написании теста, который никогда не завершается сбоем.

4. Измените код теста, чтобы новый тест был пройден. Измените функцию `SquareRoot` в файле *Rooter.cs* следующим образом:

   ```csharp
   public double SquareRoot(double x)
   {
       double estimate = x;
       double diff = x;
       while (diff > estimate / 1000)
       {
           double previousEstimate = estimate;
           estimate = estimate - (estimate * estimate - x) / (2 * estimate);
           diff = Math.Abs(previousEstimate - estimate);
       }
       return estimate;
   }
   ```

5. Выполните сборку решения, а затем в **обозревателе тестов** щелкните **Запустить все**.

   Теперь все три теста проходятся.

> [!TIP]
> Разрабатывайте код, добавляя тесты по одному. После каждой итерации проверяйте, все ли тесты завершаются успешно.

## <a name="debug-a-failing-test"></a>Отладка непройденного теста

1. Добавьте еще один тест в файл *UnitTest1.cs*:

    ```csharp
    // Verify that negative inputs throw an exception.
    [TestMethod]
    public void NegativeRangeTest()
    {
        string message;
        Rooter rooter = new Rooter();
        for (double v = -0.1; v > -3.0; v = v - 0.5)
        {
            try
            {
                // Should raise an exception:
                double actual = rooter.SquareRoot(v);

                message = String.Format("No exception for input {0}", v);
                Assert.Fail(message);
            }
            catch (ArgumentOutOfRangeException ex)
            {
                continue; // Correct exception.
            }
            catch (Exception e)
            {
                message = String.Format("Incorrect exception for {0}", v);
                Assert.Fail(message);
            }
        }
    }
    ```

2. В **обозревателе тестов** выберите **Запустить все**.

   Тест не пройден. Выберите имя теста в **обозревателе тестов**. Ошибочное проверочное утверждение будет выделено. Сообщение об ошибке отображается в области сведений **обозревателя тестов**.

   ![Сбой тестов NegativeRangeTests](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

3. Чтобы увидеть, почему тест не был пройден, выполните функцию пошагово.

    1. Установите точку останова перед функцией `SquareRoot`.

    2. В контекстном меню непройденного теста выберите **Отладить выбранные тесты**.

        Когда выполнение прекратится на точке останова, выполните код по шагам.

    3. Добавьте в метод Rooter код для перехвата исключения:

        ```csharp
        public double SquareRoot(double x)
        {
            if (x < 0.0)
            {
                throw new ArgumentOutOfRangeException();
        }
        ```

4. В обозревателе тестов выберите **Запустить все**, чтобы протестировать исправленный метод и убедиться в том, что не была добавлена регрессия.

Теперь все тесты проходят успешно.

![Все тесты пройдены](../test/media/ute_ult_alltestspass.png)

## <a name="refactor-the-code"></a>Рефакторинг кода

**Упростите основное вычисление в функции SquareRoot.**

1. Измените реализацию результата

    ```csharp
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;
    ```

2. Выберите команду **Запустить все**, чтобы протестировать подвергнутый рефакторингу метод и убедиться в том, что не была добавлена регрессия.

> [!TIP]
> Стабильный набор хороших модульных тестов придает уверенность в том, что изменение кода не привело к появлению ошибок.

**Выполните рефакторинг кода теста, чтобы исключить дублирование кода.**

Обратите внимание, что в методе `RangeTest` жестко задан знаменатель переменной `tolerance`, которая передается в метод <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>. Если планируется добавлять другие тесты, которые используют такой же расчет отклонения, использование жестко запрограммированных значений в нескольких местах может привести к ошибкам.

1. Добавьте к классу Unit1Test закрытый метод для вычисления значения отклонения, а затем вызывайте этот метод.

    ```csharp
    private double ToleranceHelper(double expected)
    {
        return expected / 1000;
    }

    ...

    [TestMethod]
    public void RangeTest()
    {
        ...
        // old code
        // double tolerance = expected/1000;
        // new code
        double tolerance = ToleranceHelper(expected);
        Assert.AreEqual(expected, actual, tolerance);
    }
    ...
    ```

2. Выберите команду **Запустить все**, чтобы протестировать подвергнутый рефакторингу метод и убедиться, что не была добавлена ошибка.

> [!NOTE]
> При добавлении вспомогательного метода в тестовый класс, который не должен отображаться в **обозревателе тестов**, не добавляйте к этому методу атрибут <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>.