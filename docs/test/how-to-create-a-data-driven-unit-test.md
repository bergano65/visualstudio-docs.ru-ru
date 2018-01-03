---
title: "Практическое руководство. Создание модульного теста, управляемого данными | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.test.testresults.unittest.datadriven
- vs.test.testresults.unittest.datadriven.failure
helpviewer_keywords:
- unit tests, running
- unit tests, data-driven
- data-driven unit tests
ms.assetid: a0322bc5-02c8-4f9f-af43-100a60b1bd28
caps.latest.revision: "33"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: f0d0250e2810adc8fd79239aa8e0807b04bbf0a3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-data-driven-unit-test"></a>Практическое руководство. Создание модульного теста, управляемого данными
Используя платформу модульного тестирования Майкрософт для управляемого кода, можно настроить метод модульного теста для получения значений из источника данных, которые впоследствии будут использоваться в методе теста. Этот метод последовательно выполняется для каждой строки в источнике данных, что облегчает тестирование разнообразных входных данных с помощью одного метода.  
  
 В этом разделе содержатся следующие подразделы.  
  
-   [Тестируемый метод](../test/how-to-create-a-data-driven-unit-test.md#BKMK_The_method_under_test)  
  
-   [Создание источника данных](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Creating_a_data_source)  
  
-   [Добавление TestContext в тестовый класс](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Adding_a_TestContext_to_the_test_class)  
  
-   [Написание метода теста](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Writing_the_test_method)  
  
    -   [Определение DataSourceAttribute](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Specifying_the_DataSourceAttribute)  
  
    -   [Использование TestContext.DataRow для доступа к данным](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Using_TestContext_DataRow_to_access_the_data)  
  
-   [Выполнение теста и просмотр результатов](../test/how-to-create-a-data-driven-unit-test.md#BKMK_Running_the_test_and_viewing_results)  
  
 Создание управляемого данными модульного теста включает в себя указанные ниже шаги.  
  
1.  Создайте источник данных, в котором содержатся значения, используемые в методе теста. Источник данных может быть любого типа, который зарегистрирован на компьютере, где выполняется тест.  
  
2.  Добавьте частное поле <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> и общее свойство `TestContext` в тестовый класс.  
  
3.  Создайте метод модульного теста и добавьте к нему атрибут <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>.  
  
4.  Используйте свойство индексатора <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> для получения значений, используемых в тесте.  
  
##  <a name="BKMK_The_method_under_test"></a> Тестируемый метод  
 Например, допустим, что были созданы следующие объекты:  
  
1.  решение с именем `MyBank`, которое принимает и обрабатывает транзакции для различных типов счетов;  
  
2.  проект в `MyBank` с именем `BankDb`, который управляет транзакциями для счетов;  
  
3.  класс с именем `Maths` в проекте `DbBank`, выполняющий математические функции, позволяющие убедиться в том, что любая транзакция выгодна банку;  
  
4.  проект модульного теста с именем `BankDbTests` для тестирования функциональности компонента `BankDb`;  
  
5.  класс модульного теста с именем `MathsTests` для проверки функциональности класса `Maths`.  
  
 Мы проверяем метод в `Maths`, который складывает два целых числа с помощью цикла:  
  
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
 Чтобы проверить метод `AddIntegers`, создадим источник данных, определяющий диапазон значений для параметров и ожидаемую возвращаемую сумму. В нашем примере создадим базу данных SQL Compact с именем `MathsData` и таблицу с именем `AddIntegersData`, которая содержит следующие имена столбцов и значений:  
  
|FirstNumber|SecondNumber|Sum|  
|-----------------|------------------|---------|  
|0|1|1|  
|1|1|2|  
|2|-3|-1|  
  
##  <a name="BKMK_Adding_a_TestContext_to_the_test_class"></a> Добавление TestContext в тестовый класс  
 Платформа модульного тестирования создает объект `TestContext` для хранения информации из источника данных для теста, управляемого данными. Затем платформа присваивает этому объекту значение свойства `TestContext`, которое мы создаем.  
  
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
 Метод теста для `AddIntegers` достаточно прост. Для каждой строки в источнике данных вызываем `AddIntegers` со значениями столбцов **FirstNumber** и **SecondNumber** в качестве параметров и сверяем возвращаемое значение со значением столбца **Sum**:  
  
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
  
 Обратите внимание, что метод `Assert` содержит сообщение, которое отображает значения `x` и `y` итерации, в которой произошел сбой. По умолчанию утвержденные значения `expected` и `actual` уже содержатся в сведениях неудачного теста.  
  
###  <a name="BKMK_Specifying_the_DataSourceAttribute"></a> Определение DataSourceAttribute  
 Атрибут `DataSource` задает строку подключения для источника данных и имя таблицы, которая используется в методе теста. Точные сведения в строке подключения отличаются в зависимости от типа используемого источника данных. В этом примере используется база данных SqlServerCe.  
  
```  
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]  
```  
  
 Атрибут DataSource имеет три конструктора.  
  
```  
[DataSource(dataSourceSettingName)]  
```  
  
 Конструктор с одним параметром использует информацию о подключении, хранящуюся в файле app.config решения. В файле конфигурации XML-элемент с именем *dataSourceSettingsName* содержит в себе информацию о подключении.  
  
 Использование файла app.config позволяет менять расположение источника данных, и при этом не вносить изменения в сам модульный тест. Дополнительные сведения о создании и использовании файла app.config см. в разделе [Пошаговое руководство. Использование файла конфигурации для определения источника данных](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).  
  
```  
[DataSource(connectionString, tableName)]  
```  
  
 Конструктор `DataSource` с двумя параметрами задает строку подключения к источнику данных и имя таблицы, содержащей данные для метода теста.  
  
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
 Для доступа к данным в таблице `AddIntegersData` используйте индексатор `TestContext.DataRow`. `DataRow` является объектом <xref:System.Data.DataRow>, поэтому значения столбца извлекаются по индексу или имени столбца. Так как значения возвращаются в виде объектов, необходимо преобразовать их в соответствующий тип.  
  
```  
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);  
  
```  
  
##  <a name="BKMK_Running_the_test_and_viewing_results"></a> Выполнение теста и просмотр результатов  
 Завершив написание метода теста, выполните сборку тестового проекта. Метод теста приводится в окне обозревателя тестов в группе **Незапускавшиеся тесты**. При запуске, написании и повторном запуске тестов в обозревателе тестов результаты отображаются в группах **Неудачные тесты**, **Пройденные тесты** и **Незапускавшиеся тесты**. Можно выбрать **Запустить все**, чтобы запустить все тесты, или **Запустить**, чтобы выбрать подмножество тестов для выполнения.  
  
 Панель результатов теста в верхней части обозревателя обновляется по мере выполнения тестов. По завершении тестового запуска область становится зеленой, если все тесты пройдены, или красной, если какой-либо из тестов не был пройден успешно. Сводка тестового запуска приводится в области сведений в нижней части окна обозревателя тестов. Выберите тест, чтобы просмотреть детальную информацию по данному тесту в нижней панели.  
  
 При выполнении метода `AddIntegers_FromDataSourceTest` в нашем примере панель результатов станет красной и метод теста переместится в группу **Неудачные тесты**. Тест, управляемый данными, завершается с ошибкой, если какая-либо итерация из источника данных завершается неудачно. При выборе неудачных тестов, управляемых данными, в окне обозревателя тестов на панели сведений выводятся результаты каждой итерации в соответствии с индексом строки данных. В этом примере оказывается, что алгоритм `AddIntegers` неправильно обрабатывает отрицательные значения.  
  
 После исправления тестируемого метода и повторного выполнения теста панель результатов станет зеленой и метод теста переместится в группу **Пройденные тесты**.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>   
 [Практическое руководство. Создание и выполнение модульного теста](http://msdn.microsoft.com/en-us/5e0f43cf-5e51-48e2-9c98-0eb9324bdc48)   
 [Модульное тестирование кода](../test/unit-test-your-code.md)   
 [Выполнение модульных тестов с помощью обозревателя тестов](../test/run-unit-tests-with-test-explorer.md)   
 [Написание модульных тестов для платформы .NET Framework с использованием платформы модульного тестирования Майкрософт для управляемого кода](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)
