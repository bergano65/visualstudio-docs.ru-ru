---
title: "Изоляция тестируемого кода с помощью Microsoft Fakes | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
dev_langs:
- VB
- CSharp
ms.openlocfilehash: 42164191a3782de31245b1bc46cddce57a56de02
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="isolating-code-under-test-with-microsoft-fakes"></a>Изоляция тестируемого кода с помощью Microsoft Fakes

Microsoft Fakes помогает изолировать тестируемый код, заменяя другие части приложения *заглушками* или *оболочками*. Это небольшие части кода, которые управляются тестами. Изолируя код для тестирования, при непрохождении теста вы будете знать, что причина лежит именно в этом коде, а не где-либо еще. Заглушки и оболочки также позволяют тестировать код, даже если другие части приложения еще не работают.

Fakes предлагает два варианта на выбор:

-   [Заглушка](#stubs) заменяет класс небольшим заменителем, реализующим тот же интерфейс.  Для использования заглушек необходимо разработать приложение таким образом, чтобы каждый компонент зависел только от интерфейса, а не от других компонентов. (В данном случае "компонент" означает класс или группу классов, которые разрабатываются и обновляются вместе и обычно содержатся в сборке.)

-   [Оболочка](#shims) изменяет скомпилированный код приложения во время выполнения, чтобы вместо заданного вызова метода он запускал код-оболочку, предоставляемый тестом. Оболочки можно использовать для замены вызовов сборок, которые невозможно изменить, например сборок .NET.

![Имитации замещают другие компоненты](../test/media/fakes-2.png "Fakes-2")  

**Требования**

-   Visual Studio Enterprise

## <a name="choosing-between-stub-and-shim-types"></a>Выбор между заглушкой и оболочкой  
Обычно проект Visual Studio считается компонентом, потому что эти классы разрабатываются и обновляются одновременно. Заглушки и оболочки можно использовать для вызовов, осуществляемых проектом в отношении других проектов в решении или других сборок, на которые ссылается проект.  
  
Как правило, заглушки рекомендуется использовать для вызовов в пределах решения Visual Studio, а оболочки — для вызовов других сборок, на которые указывают ссылки. Это происходит потому, что в собственном решении рекомендуется отделять компоненты, указывая интерфейсы нужным заглушкам способом. Однако внешние сборки, такие как System.dll, обычно не предоставляются с отдельными определениями интерфейса, поэтому вместо них приходится использовать оболочки.  
  
Вот некоторые другие причины.  
  
**Производительность.** Оболочки выполняются медленнее, потому что они перезаписывают код во время выполнения. Заглушки не приводят к снижению производительности и выполняются так же быстро, как и виртуальные методы.  
  
**Статические методы, запечатанные типы.** Заглушки можно использовать только для реализации интерфейсов. Таким образом, типы заглушек невозможно использовать для статических методов, невиртуальных методов, запечатанных виртуальных методов, методов в запечатанных типах и т. д.  
  
**Внутренние типы.** Как заглушки, так и оболочки можно использовать с внутренними типами, доступ к которым предоставляется посредством атрибута сборки <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.  
  
**Закрытые методы.** Оболочки могут заменять вызовы закрытых методов, если все типы в сигнатуре метода являются видимыми. Заглушки могут заменять только видимые методы.  
  
**Интерфейсы и абстрактные методы.** Заглушки позволяют реализовывать интерфейсы и абстрактные методы, которые можно использовать при тестировании. Оболочки не могут реализовать интерфейсы и абстрактные методы, поскольку они не имеют тел методов.  
  
Как правило, типы заглушек рекомендуется использовать для изоляции от зависимостей в базе кода. Для этого можно скрыть компоненты за интерфейсами. Типы оболочек можно использовать для изоляции от сторонних компонентов, которые не предоставляют пригодного для тестирования API.  
  
##  <a name="stubs"></a> Начало работы с заглушками  
Дополнительные сведения см. в разделе [Использование заглушек для изоляции частей приложений друг от друга при модульном тестировании](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).  
  
1.  **Вставка интерфейсов**  
  
     Для использования заглушек необходимо написать код, который требуется протестировать таким образом, чтобы он явно не упоминал классы в другом компоненте приложения. В данном случае "компонент" значит класс или классы, которые разрабатываются и обновляются вместе и обычно содержатся в одном проекте Visual Studio. Переменные и параметры должны быть объявлены с помощью интерфейсов, а экземпляры других компонентов должны быть переданы в фабрику или созданы с ее помощью. Например, если StockFeed — это класс в другом компоненте приложения, то следующий код будет считаться неудачным.  
  
     `return (new StockFeed()).GetSharePrice("COOO"); // Bad`  
  
     Вместо этого определите интерфейс, который может быть реализован другим компонентом или заглушкой в целях тестирования.  
  
    ```csharp  
    public int GetContosoPrice(IStockFeed feed)  
    { return feed.GetSharePrice("COOO"); }  
  
    ```  
  
    ```vb  
    Public Function GetContosoPrice(feed As IStockFeed) As Integer  
     Return feed.GetSharePrice("COOO")  
    End Function  
  
    ```  
  
2.  **Добавление сборки Fakes**  
  
    1.  В обозревателе решений разверните список ссылок тестового проекта. При использовании Visual Basic нужно щелкнуть **Показать все файлы**, чтобы открыть список ссылок.  
  
    2.  Выберите ссылку на сборку, в которой определен интерфейс (например, IStockFeed). В контекстном меню данной ссылки щелкните **Добавить сборку имитаций**.  
  
    3.  Выполните повторную сборку решения.  
  
3.  В тестах создайте экземпляры заглушки и предоставьте код для ее методов.  
  
    ```csharp  
    [TestClass]  
    class TestStockAnalyzer  
    {  
        [TestMethod]  
        public void TestContosoStockPrice()  
        {  
          // Arrange:  
  
            // Create the fake stockFeed:  
            IStockFeed stockFeed =   
                 new StockAnalysis.Fakes.StubIStockFeed() // Generated by Fakes.  
                     {  
                         // Define each method:  
                         // Name is original name + parameter types:  
                         GetSharePriceString = (company) => { return 1234; }  
                     };  
  
            // In the completed application, stockFeed would be a real one:  
            var componentUnderTest = new StockAnalyzer(stockFeed);  
  
          // Act:  
            int actualValue = componentUnderTest.GetContosoPrice();  
  
          // Assert:  
            Assert.AreEqual(1234, actualValue);  
        }  
        ...  
    }  
    ```  
  
    ```vb  
    <TestClass()> _  
    Class TestStockAnalyzer  
  
        <TestMethod()> _  
        Public Sub TestContosoStockPrice()  
            ' Arrange:  
            ' Create the fake stockFeed:  
            Dim stockFeed As New StockAnalysis.Fakes.StubIStockFeed  
            With stockFeed  
                .GetSharePriceString = Function(company)  
                                           Return 1234  
                                       End Function  
            End With  
            ' In the completed application, stockFeed would be a real one:  
            Dim componentUnderTest As New StockAnalyzer(stockFeed)  
            ' Act:  
            Dim actualValue As Integer = componentUnderTest.GetContosoPrice  
            ' Assert:  
            Assert.AreEqual(1234, actualValue)  
        End Sub  
    End Class  
  
    ```  
  
    Особую роль здесь играет класс `StubIStockFeed`. Для каждого интерфейса в сборке, на которую указывает ссылка, механизм Microsoft Fakes создаст класс заглушки. Имя класса заглушки является производным от имени интерфейса, где `Fakes.Stub` — это префикс, за которым следуют имена типов параметров.  
  
    Заглушки также создаются для методов получения и задания свойств, для событий и для универсальных методов. Дополнительные сведения см. в разделе [Использование заглушек для изоляции частей приложений друг от друга при модульном тестировании](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).  
  
##  <a name="shims"></a> Начало работы с оболочками  
(Дополнительные сведения см. в разделе [Использование оболочек совместимости для изоляции приложения от других сборок при модульном тестировании](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).)  
  
Предположим, что компонент содержит вызовы `DateTime.Now`.  
  
```csharp  
// Code under test:  
    public int GetTheCurrentYear()  
    {  
       return DateTime.Now.Year;  
    }  
  
```  
  
Во время тестирования потребовалось заменить свойство `Now` оболочкой, поскольку реальная версия при каждом вызове возвращает разные значения, что создает неудобства.  
  
Для использования оболочек не следует изменять код приложения или писать его определенным способом.  
  
1.  **Добавление сборки Fakes**  
  
     В обозревателе решений откройте ссылки проекта модульного теста и выберите ссылку на сборку, содержащую метод, который требуется имитировать. В этом примере класс `DateTime` находится в файле **System.dll**.  Чтобы просмотреть ссылки в проекте Visual Basic, щелкните **Показать все файлы**.  
  
     Выберите **Добавить сборку имитаций**.  
  
2.  **Вставка оболочки в ShimsContext**  
  
    ```csharp  
    [TestClass]  
    public class TestClass1  
    {   
            [TestMethod]  
            public void TestCurrentYear()  
            {  
                int fixedYear = 2000;  
  
                // Shims can be used only in a ShimsContext:  
                using (ShimsContext.Create())  
                {  
                  // Arrange:  
                    // Shim DateTime.Now to return a fixed date:  
                    System.Fakes.ShimDateTime.NowGet =   
                    () =>  
                    { return new DateTime(fixedYear, 1, 1); };  
  
                    // Instantiate the component under test:  
                    var componentUnderTest = new MyComponent();  
  
                  // Act:  
                    int year = componentUnderTest.GetTheCurrentYear();  
  
                  // Assert:   
                    // This will always be true if the component is working:  
                    Assert.AreEqual(fixedYear, year);  
                }  
            }  
    }
    ```

    ```vb  
    <TestClass()> _  
    Public Class TestClass1  
        <TestMethod()> _  
        Public Sub TestCurrentYear()  
            Using s = Microsoft.QualityTools.Testing.Fakes.ShimsContext.Create()  
                Dim fixedYear As Integer = 2000  
                ' Arrange:  
                ' Detour DateTime.Now to return a fixed date:  
                System.Fakes.ShimDateTime.NowGet = _  
                    Function() As DateTime  
                        Return New DateTime(fixedYear, 1, 1)  
                    End Function  
  
                ' Instantiate the component under test:  
                Dim componentUnderTest = New MyComponent()  
                ' Act:  
                Dim year As Integer = componentUnderTest.GetTheCurrentYear  
                ' Assert:   
                ' This will always be true if the component is working:  
                Assert.AreEqual(fixedYear, year)  
            End Using  
        End Sub  
    End Class  
    ```  

    Имена классов оболочки создаются путем добавления префикса `Fakes.Shim` к имени исходного типа. Имена параметров добавляются к имени метода. (Ссылки на сборки в System.Fakes можно не добавлять.)  

В предыдущем примере использовалась оболочка для статического метода. Чтобы использовать оболочку для метода экземпляра, вставьте `AllInstances` между именем типа и именем метода.  

```  
System.IO.Fakes.ShimFile.AllInstances.ReadToEnd = ...  
```  

(Нет сборки System.IO.Fakes для ссылки. Пространство имен создается в процессе создания оболочки. Однако можно использовать using или Import обычным способом.)  

Можно также создать оболочки для отдельных экземпляров, конструкторов и свойств. Дополнительные сведения см. в разделе [Использование оболочек совместимости для изоляции приложения от других сборок при модульном тестировании](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).  

## <a name="in-this-section"></a>Содержание раздела  
 [Использование заглушек для изоляции частей приложений друг от друга при модульном тестировании](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md)  
  
 [Использование оболочек совместимости для изоляции приложения от других сборок при модульном тестировании](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)  
  
 [Формирование и компиляция кода, а также соглашения об именовании в Microsoft Fakes](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md)
