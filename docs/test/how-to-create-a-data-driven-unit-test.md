---
title: Создание модульного теста, управляемого данными
description: Сведения о том, как с помощью платформы модульного тестирования Майкрософт для управляемого кода настроить метод модульного теста для получения значений из источника данных.
ms.custom: SEO-VS-2020
ms.date: 05/08/2019
ms.topic: how-to
f1_keywords:
- vs.test.testresults.unittest.datadriven
- vs.test.testresults.unittest.datadriven.failure
helpviewer_keywords:
- unit tests, running
- unit tests, data-driven
- data-driven unit tests
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 94dcc3aed8d41f9ece0f9b51410fc749330b01df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966699"
---
# <a name="how-to-create-a-data-driven-unit-test"></a>Практическое руководство. создание модульного теста, управляемого данными

Вы можете использовать платформу модульного тестирования Майкрософт для управляемого кода, чтобы настроить метод модульного теста для получения значений из источника данных. Этот метод последовательно выполняется для каждой строки в источнике данных, что облегчает тестирование разнообразных входных данных с помощью одного метода.

Создание управляемого данными модульного теста включает в себя указанные ниже шаги.

1. Создайте источник данных, в котором содержатся значения, используемые в методе теста. Источник данных может быть любого типа, который зарегистрирован на компьютере, где выполняется тест.

2. Добавьте частное поле <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> и общее свойство `TestContext` в тестовый класс.

3. Создайте метод модульного теста и добавьте к нему атрибут <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>.

4. Используйте свойство индексатора <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> для получения значений, используемых в тесте.

## <a name="the-method-under-test"></a>Тестируемый метод

Например, допустим, что у вас есть:

1. решение с именем `MyBank`, которое принимает и обрабатывает транзакции для различных типов счетов;

2. проект в `MyBank` с именем `BankDb`, который управляет транзакциями для счетов;

3. класс с именем `Maths` в проекте `BankDb`, выполняющий математические функции, позволяющие убедиться в том, что любая транзакция выгодна банку;

4. проект модульного теста с именем `BankDbTests` для тестирования функциональности компонента `BankDb`;

5. класс модульного теста с именем `MathsTests` для проверки функциональности класса `Maths`.

Мы проверяем метод в `Maths`, который складывает два целых числа с помощью цикла:

```csharp
public int AddIntegers(int first, int second)
{
    int sum = first;
    for( int i = 0; i < second; i++)
    {
        sum += 1;
    }
    return sum;
}
```

## <a name="create-a-data-source"></a>Создание источника данных

Чтобы проверить метод `AddIntegers`, создайте источник данных, определяющий диапазон значений для параметров и ожидаемую возвращаемую сумму. В этом примере мы создадим базу данных SQL Compact с именем `MathsData` и таблицу с именем `AddIntegersData`, которая содержит следующие имена столбцов и значения:

|FirstNumber|SecondNumber|SUM|
|-|------------------|-|
|0|1|1|
|1|1|2|
|2|–3|-1|

## <a name="add-a-testcontext-to-the-test-class"></a>Добавление TestContext в тестовый класс

Платформа модульного тестирования создает объект `TestContext` для хранения информации из источника данных для теста, управляемого данными. Затем платформа присваивает этому объекту значение создаваемого свойства `TestContext`.

```csharp
private TestContext testContextInstance;
public TestContext TestContext
{
    get { return testContextInstance; }
    set { testContextInstance = value; }
}
```

В методе теста получить доступ к данным можно через свойство индексатора `DataRow``TestContext`.

> [!NOTE]
> .NET Core не поддерживает атрибут [DataSource](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute). При попытке получить доступ к данным тестирования таким образом в проекте модульного теста для .NET Core или универсальной платформы Windows вы увидите сообщение об ошибке **"'TestContext' не содержит определение для 'DataRow', и доступный метод расширения 'DataRow', принимающий первый аргумент типа 'TestContext', не найден (возможно, отсутствует директива using или ссылка на сборку?)"**.

## <a name="write-the-test-method"></a>Написание метода теста

Метод теста для `AddIntegers` достаточно прост. Для каждой строки в источнике данных вызовите `AddIntegers` со значениями столбцов **FirstNumber** и **SecondNumber** в качестве параметров и сверьте возвращаемое значение со значением столбца **Sum**:

```csharp
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0; Data Source=C:\Data\MathsData.sdf;", "Numbers")]
[TestMethod()]
public void AddIntegers_FromDataSourceTest()
{
    var target = new Maths();

    // Access the data
    int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
    int y = Convert.ToInt32(TestContext.DataRow["SecondNumber"]);
    int expected = Convert.ToInt32(TestContext.DataRow["Sum"]);
    int actual = target.IntegerMethod(x, y);
    Assert.AreEqual(expected, actual,
        "x:<{0}> y:<{1}>",
        new object[] {x, y});
}
```

Метод `Assert` содержит сообщение, которое отображает значения `x` и `y` итерации, в которой произошел сбой. По умолчанию утвержденные значения `expected` и `actual` уже содержатся в сведениях неудачного теста.

### <a name="specify-the-datasourceattribute"></a>Определение DataSourceAttribute

Атрибут `DataSource` задает строку подключения для источника данных и имя таблицы, которая используется в методе теста. Точные сведения в строке подключения отличаются в зависимости от типа используемого источника данных. В этом примере используется база данных SqlServerCe.

```csharp
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]
```

Атрибут DataSource имеет три конструктора.

```csharp
[DataSource(dataSourceSettingName)]
```

Конструктор с одним параметром использует информацию о подключении, хранящуюся в файле *app.config* решения. В файле конфигурации XML-элемент с именем *dataSourceSettingsName* содержит в себе информацию о подключении.

Использование файла *app.config* позволяет менять расположение источника данных и при этом не вносить изменения в сам модульный тест. Дополнительные сведения о создании и использовании файла *app.config* см. в статье [Пошаговое руководство. Использование файла конфигурации для определения источника данных](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).

```csharp
[DataSource(connectionString, tableName)]
```

Конструктор `DataSource` с двумя параметрами задает строку подключения к источнику данных и имя таблицы, содержащей данные для метода теста.

Строки подключения зависят от типа источника данных, но они должны содержать элемент Provider, который определяет неизменяемое имя поставщика данных.

```csharp
[DataSource(
    dataProvider,
    connectionString,
    tableName,
    dataAccessMethod
    )]
```

### <a name="use-testcontextdatarow-to-access-the-data"></a>Использование TestContext.DataRow для доступа к данным

Для доступа к данным в таблице `AddIntegersData` используйте индексатор `TestContext.DataRow`. `DataRow` является объектом <xref:System.Data.DataRow>, поэтому значения столбца извлекаются по индексу или имени столбца. Так как значения возвращаются в виде объектов, преобразуйте их в соответствующий тип.

```csharp
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
```

## <a name="run-the-test-and-view-results"></a>Запуск теста и просмотр результатов

Завершив написание метода теста, выполните сборку тестового проекта. Метод теста приводится в **обозревателе тестов** в группе **Не запускавшиеся тесты**. При запуске, написании и повторном запуске тестов в **обозревателе тестов** результаты отображаются в группах **Неудачные тесты**, **Пройденные тесты** и **Незапускавшиеся тесты**. Можно выбрать **Запустить все** , чтобы запустить все тесты, или выбрать **Запустить** , чтобы выбрать подмножество тестов для запуска.

Панель результатов теста в верхней части **обозревателя тестов** обновляется по мере выполнения тестов. По завершении тестового запуска область становится зеленой, если все тесты пройдены, или красной, если какой-либо из тестов не был пройден успешно. Сводка тестового запуска приводится в области сведений в нижней части окна **обозревателя тестов**. Выберите тест, чтобы просмотреть детальную информацию по данному тесту в нижней панели.

> [!NOTE]
> Показан результат для каждой строки данных, а также один сводный результат. Если тест пройден для каждой строки данных, в сводке отображается **Пройдено**. Если тест не пройден для какой-то строки данных, в сводке отображается **Не пройдено**.

При выполнении метода `AddIntegers_FromDataSourceTest` в нашем примере панель результатов станет красной, а метод теста переместится в группу **Неудачные тесты**. Тест, управляемый данными, завершается с ошибкой, если какая-либо итерация из источника данных завершается неудачно. При выборе неудачных тестов, управляемых данными, в окне **обозревателя тестов** на панели сведений выводятся результаты каждой итерации в соответствии с индексом строки данных. В этом примере оказывается, что алгоритм `AddIntegers` неправильно обрабатывает отрицательные значения.

После исправления тестируемого метода и повторного выполнения теста панель результатов станет зеленой и метод теста переместится в группу **Пройденные тесты**.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>
- [Модульное тестирование кода](../test/unit-test-your-code.md)
- [Выполнение модульных тестов с помощью обозревателя тестов](../test/run-unit-tests-with-test-explorer.md)
- [Написание модульных тестов для .NET с использованием платформы модульного тестирования Майкрософт](../test/unit-test-your-code.md)
