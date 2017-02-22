---
title: "Практическое руководство. Создание модульного теста, управляемого данными | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.test.testresults.unittest.datadriven"
  - "vs.test.testresults.unittest.datadriven.failure"
helpviewer_keywords: 
  - "модульные тесты, выполнение"
  - "модульные тесты, управляемые данными"
  - "модульные тесты, управляемые данными"
ms.assetid: a0322bc5-02c8-4f9f-af43-100a60b1bd28
caps.latest.revision: 33
caps.handback.revision: 33
ms.author: "mlearned"
manager: "douge"
---
# Практическое руководство. Создание модульного теста, управляемого данными
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Используя платформу модульного тестирования Microsoft для управляемого кода, можно настроить метод модульного теста для получения значений из источника данных, которые впоследствии будут использоваться в методе теста.  Этот метод последовательно запускается для каждой строки в источнике данных, что облегчает тестирование разнообразных входных данных с помощью одного метода.  
  
 В этом разделе содержатся следующие подразделы.  
  
-   [Тестируемый метод](../test/how-to-create-a-data-driven-unit-test.md#BKMK_The_method_under_test)  
  
-   [Создание источника данных](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Creating_a_data_source)  
  
-   [Добавление TestContext в тестовый класс](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Adding_a_TestContext_to_the_test_class)  
  
-   [Написание метода теста](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Writing_the_test_method)  
  
    -   [Определение DataSourceAttribute](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Specifying_the_DataSourceAttribute)  
  
    -   [Использование TestContext.DataRow для доступа к данным](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Using_TestContext_DataRow_to_access_the_data)  
  
-   [Выполнение теста и просмотр результатов](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Running_the_test_and_viewing_results)  
  
 Создание управляемого данными модульного теста включает в себя следующие шаги:  
  
1.  Создайте источник данных, в котором содержатся значения, используемые в методе теста.  Источник данных может быть любого типа, который зарегистрирован на компьютере, где выполняется тест.  
  
2.  Добавьте закрытое поле <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> и открытое свойство `TestContext` в тестовый класс.  
  
3.  Создайте метод модульного теста и добавьте к нему атрибут <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>.  
  
4.  Используйте свойство индексатора <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> для получения значений, используемых в тесте.  
  
##  <a name="BKMK_The_method_under_test"></a> Тестируемый метод  
 Например, допустим, что было создано:  
  
1.  Решение с названием `MyBank`, которое принимает и обрабатывает транзакции для различных типов учетных записей.  
  
2.  Проект в `MyBank` с названием `BankDb`, который управляет транзакциями для учетных записей.  
  
3.  Класс с названием `Maths` в проекте `DbBank`, выполняющий математические функции, позволяющие убедиться, что любая транзакция выгодна банку.  
  
4.  Проект модульных тестов с названием `BankDbTests` для тестирования функциональности компонента `BankDb`.  
  
5.  Класс модульного теста с названием `MathsTests` для проверки функциональности класса `Maths`.  
  
 Мы проверяем метод в `Maths`, который складывает 2 целых числа с помощью цикла:  
  
```  
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
  
##  <a name="BKMK_Creating_a_data_source"></a> Создание источника данных  
 Чтобы проверить метод `AddIntegers`, создадим источник данных, определяющий диапазон значений для параметров и ожидаемых возвращенных значений суммы.  В нашем примере, создадим базу данных Sql Compact с названием `MathsData` и таблицу с названием `AddIntegersData`, которая содержит следующие имена столбцов и значений  
  
|FirstNumber|SecondNumber|Sum|  
|-----------------|------------------|---------|  
|0|1|1|  
|1|1|2|  
|2|\-3|\-1|  
  
##  <a name="BKMK_Adding_a_TestContext_to_the_test_class"></a> Добавление TestContext в тестовый класс  
 Платформа модульного тестирования создает объект `TestContext` для хранения информации из источника данных для теста, управляемого данными.  Затем платформа задает этому объекту значения свойства `TestContext`, которое мы создаем.  
  
```  
  
private TestContext testContextInstance;  
public TestContext TestContext  
{  
    get { return testContextInstance; }  
    set { testContextInstance = value; }  
}  
  
```  
  
 В методе теста получить доступ к данным можно через свойство индексатора `DataRow` `TestContext`.  
  
##  <a name="BKMK_Writing_the_test_method"></a> Написание метода теста  
 Метод теста для `AddIntegers` достаточно прост.  Для каждой строки в источнике данных вызываем `AddIntegers` со значениями столбцов **FirstNumber** и **SecondNumber** в качестве параметров и сверяем возвращаемое значение со значением столбца **Sum**:  
  
```  
  
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
  
 Обратите внимание, что метод `Assert` содержит сообщение, которое отображает значения `x` и `y` итерации, на которой произошел сбой.  По умолчанию утвержденные значения `expected` и `actual` уже содержатся в сведениях неудачного теста.  
  
###  <a name="BKMK_Specifying_the_DataSourceAttribute"></a> Определение DataSourceAttribute  
 Атрибут `DataSource` задает строку подключения для источника данных и название таблицы, которая используется в методе теста.  Точные сведения в строке подключения отличаются, в зависимости от используемого типа источника данных.  В этом примере используется база данных SqlServerCe.  
  
```  
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]  
```  
  
 Атрибут источника данных имеет 3 конструктора.  
  
```  
[DataSource(dataSourceSettingName)]  
```  
  
 Конструктор с одним параметром использует информацию о соединении, хранящуюся в конфигурационном файле решения app.config.  В файле конфигурации Xml элемент с названием *dataSourceSettingsName* содержит в себе информацию о подключении.  
  
 Использование файла app.config позволяет менять расположение источника данных, и при этом не вносить изменения в сам модульный тест.  Дополнительные сведения о создании и использовании файла app.config см. в разделе [Пошаговое руководство. Использование файла конфигурации для определения источника данных](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)  
  
```  
[DataSource(connectionString, tableName)]  
```  
  
 Конструктор `DataSource` с двумя параметрами, которые задают строку подключения к источнику данных и название таблицы, содержащую данные для метода теста.  
  
 Строки подключения зависят от типа источника данных, но они должны содержать элемент Provider, который определяет неизменяемое имя поставщика данных.  
  
```  
[DataSource(  
    dataProvider,   
    connectionString,   
    tableName,  
    dataAccessMethod  
    )]  
```  
  
###  <a name="BKMK_Using_TestContext_DataRow_to_access_the_data"></a> Использование TestContext.DataRow для доступа к данным  
 Для доступа к данным таблицы `AddIntegersData` используйте индексатор `TestContext.DataRow`.  `DataRow` является объектом <xref:System.Data.DataRow>, поэтому значения столбца извлекаются по индексу или названию столбца.  Поскольку значения возвращаются в виде объектов, необходимо преобразовать их к соответствующему типу.  
  
```  
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);  
  
```  
  
##  <a name="BKMK_Running_the_test_and_viewing_results"></a> Выполнение теста и просмотр результатов  
 После завершения написания метода теста, выполните построение тестового проекта.  Метод теста отображается в окне обозревателя тестов в группе **Незапускавшиеся тесты**.  При запуске, написании и повторном запуске тестов, обозреватель тестов отображает результаты в группах: **Неудачные тесты**, **Пройденные тесты** и **Незапускавшиеся тесты**.  Можно нажать **Выполнить все**, чтобы выполнить все тесты или нажать **Выполнить...** для выбора подмножества тестов для выполнения.  
  
 Панель результатов теста в верхней части обозревателя обновляется по мере выполнения тестов.  По завершению тестового запуска, область становится зеленой, если все тесты пройдены или красной, если какой\-либо из тестов был завершен с ошибкой.  Сводка тестового запуска отображается в информационной области в нижней части окна обозревателя тестов.  Выберите тест, чтобы просмотреть подробные сведения по нему в нижней панели.  
  
 При запуске метода `AddIntegers_FromDataSourceTest` в нашем примере панель результатов станет красной и метод теста переместится в **Неудачные тесты**. Тест, управляемый данными, завершается с ошибкой, если какая\-либо итерация из источника данных завершается неудачно.  При выборе неудачных тестов, управляемых данными, в окне обозревателя тестов, панель с подробными данными отображает результаты каждой итерации в соответствии с индексом строки данных.  В данном примере оказывается, что алгоритм `AddIntegers` неправильно обрабатывает отрицательные значения.  
  
 После исправления тестируемого метода и повторного выполнения теста, панель результатов станет зеленой и метод теста переместится в группу **Пройденные тесты**.  
  
## См. также  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>   
 [Практическое руководство. Создание и выполнение модульного теста](http://msdn.microsoft.com/ru-ru/5e0f43cf-5e51-48e2-9c98-0eb9324bdc48)   
 [Модульное тестирование кода](../test/unit-test-your-code.md)   
 [Выполнение модульных тестов с помощью обозревателя тестов](../test/run-unit-tests-with-test-explorer.md)   
 [Написание модульных тестов для платформы .NET Framework с использованием платформы модульного тестирования Майкрософт для управляемого кода](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)