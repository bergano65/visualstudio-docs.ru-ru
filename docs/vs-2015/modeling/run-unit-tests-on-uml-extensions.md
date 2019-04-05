---
title: Выполнение модульных тестов для расширений UML | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 745d74ae-e48c-4fd9-a755-4354b81b9f8a
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 493193e24fcee2b3f3290546abc656faee7d88a7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992753"
---
# <a name="run-unit-tests-on-uml-extensions"></a>Выполнение модульных тестов для расширений UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Чтобы сохранить стабильность кода при последующих изменениях, рекомендуется создать модульные тесты и выполнить их в составе обычного процесса сборки. Дополнительные сведения см. в статье [Модульное тестирование кода](../test/unit-test-your-code.md). Чтобы настроить тесты для расширений моделирования Visual Studio, вам потребуются некоторые основные сведения. В общем процедура включает перечисленные ниже задачи.  
  
- [Настройка модульного теста для расширений VSIX](#Host)  
  
   Выполните тесты с помощью адаптера IDE Visual Studio. Добавьте префикс `[HostType("VS IDE")]`для каждого метода теста. Этот адаптер запускает [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] при выполнении тестов.  
  
- [Доступ к DTE и хранилищу моделей](#DTE)  
  
   Как правило, вам потребуется открыть модель и ее схемы и получить доступ к `IModelStore` во время инициализации теста.  
  
- [Открытие схемы модели](#Opening)  
  
   Можно выполнить приведение `EnvDTE.ProjectItem` к и из `IDiagramContext`.  
  
- [Внесение изменений в потоке пользовательского интерфейса](#UiThread)  
  
   Тесты, которые вносят изменения в хранилище моделей, необходимо выполнять в потоке пользовательского интерфейса. Для этого можно использовать `Microsoft.VSSDK.Tools.VsIdeTesting.UIThreadInvoker` .  
  
- [Тестирование команд, жестов и других компонентов MEF](#MEF)  
  
   Чтобы выполнить тестирование компонентов MEF, необходимо явно соединить их импортированные свойства со значениями.  
  
  Эти моменты рассматриваются в следующих разделах.  
  
  Пример модульного тестирования расширения UML можно найти в галерее примеров кода на странице [UML — быстрый текстовый ввод](http://code.msdn.microsoft.com/UML-Rapid-Entry-using-Text-0813ad8a).  
  
## <a name="requirements"></a>Требования  
 См. раздел [Требования](../modeling/extend-uml-models-and-diagrams.md#Requirements).  
  
 Чтобы узнать, какие версии Visual Studio поддерживают эту функцию, см. раздел [Поддержка версий для инструментов моделирования и архитектуры](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
##  <a name="Host"></a> Настройка модульного теста для расширений VSIX  
 Методы в расширении моделирования обычно работают с уже открытой схемой. Методы используют свойства импорта MEF, такие как **IDiagramContext** и **ILinkedUndoContext**. Этот контекст должен быть настроен в тестовой среде, прежде чем вы сможете выполнять тесты.  
  
#### <a name="to-set-up-a-unit-test-that-executes-in-includevsprvsincludesvsprvs-mdmd"></a>Настройка модульного теста, который выполняется в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
1.  Создайте проект расширения UML и проект модульного теста.  
  
    1.  **Проект расширения UML.** Как правило, он создается с помощью команд, жестов или шаблонов проектов проверки. Например, см. в разделе [определение команды меню на схеме моделирования](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
    2.  **Проект модульного теста.** Дополнительные сведения см. в статье [Модульное тестирование кода](../test/unit-test-your-code.md).  
  
2.  Создайте решение [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , которое содержит проект моделирования UML. Вы будете использовать это решение как исходное состояние тестов. Его необходимо отделить от решения, в котором создано расширение UML и его модульные тесты. Дополнительные сведения см. в разделе [UML Создание проектов и схем моделирования](../modeling/create-uml-modeling-projects-and-diagrams.md).  
  
3.  **В проекте расширения UML**внесите изменения в CSPROJ-файл в текстовом режиме и убедитесь, что в следующих строках отображается значение `true`:  
  
    ```  
    <CopyBuildOutputToOutputDirectory>true</CopyBuildOutputToOutputDirectory>  
        <CopyOutputSymbolsToOutputDirectory>true</CopyOutputSymbolsToOutputDirectory>  
    ```  
  
     Чтобы изменить CSPROJ-файл в текстовом режиме, в контекстном меню проекта в Обозревателе решений выберите пункт **Выгрузить проект** . Затем выберите **Изменить…CSPROJ**. После внесения изменений в текст выберите **Перезагрузить проект**.  
  
4.  В проекте расширения UML добавьте в **Properties\AssemblyInfo.cs**следующую строку. Это позволит модульным тестам получать доступ к методам, которые необходимо протестировать:  
  
    ```csharp  
    [assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.  
    ```  
  
5.  **В проекте модульного теста**добавьте следующие ссылки на сборки:  
  
    -   *Проект расширения UML*  
  
    -   **EnvDTE.dll**  
  
    -   **Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll**  
  
    -   **Microsoft.VisualStudio.ComponentModelHost.dll**  
  
    -   **Microsoft.VisualStudio.QualityTools.UnitTestFramework.dll**  
  
    -   **Microsoft.VisualStudio.Uml.Interfaces.dll**  
  
    -   **Microsoft.VSSDK.TestHostFramework.dll**  
  
6.  Добавьте атрибут `[HostType("VS IDE")]` в качестве префикса во все методы теста, включая методы инициализации.  
  
     Это позволит гарантировать, что тест будет выполняться в экспериментальном экземпляре Visual Studio.  
  
##  <a name="DTE"></a> Доступ к DTE и хранилищу моделей  
 Создайте метод для открытия проекта моделирования в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Как правило, решение потребуется открывать только однократно в каждом тестовом запуске. Чтобы выполнять метод только один раз, добавьте в качестве префикса метода атрибут `[AssemblyInitialize]` . Не забывайте, что атрибут [HostType("VS IDE")] также должен быть добавлен в каждый метод теста.  Пример:  
  
```csharp  
using EnvDTE;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.TestTools.UnitTesting;  
using Microsoft.VSSDK.Tools.VsIdeTesting;  
  
namespace UnitTests  
{  
  [TestClass]  
  public static class TestSetup  
  {  
  
    // Location of a VS Solution that defines an initial state for your tests:  
    private const string testSolutionFilePath = @"C:\MyTestFolder\TestModelSln\TestModel.sln";  
    // Name of a modeling project within the test solution:  
    private const string testModelingProjectName = "MyTestModel";  
  
    // Make Solution and IModelStore available to test methods:  
    public static Solution ModelSolution = null;  
    public static IModelingProject ModelingProject = null;  
    public static IModelStore ModelStore = null;  
  
    // This method will be performed once to initialize tests for this assembly:  
    [AssemblyInitialize]   
    [HostType("VS IDE")]  
    public static void OpenTestModelingProject(TestContext testContext)  
    {  
      // To make sure that we always start the tests in the same state,  
      // copy the test solution from a read-only directory:  
      // TODO: copy test solution folder.  
  
      // Open a solution that is the initial state for your tests:  
      ModelSolution = VsIdeTestHostContext.Dte.Solution;  
      ModelSolution.Open(testSolutionFilePath);  
  
      // Find the ModelingProject and IModelStore:  
      foreach (Project project in ModelSolution.Projects)  
      {  
        // http://msdn.microsoft.com/library/ee791691.aspx  
        ModelingProject = project as IModelingProject;  
        if (ModelingProject != null)  
        {  
          // This is a modeling project.  
          ModelStore = ModelingProject.Store;  
          break;  
        }  
        // else this is another kind of project.  
      }  
  
      Assert.IsNotNull(ModelSolution, "VS solution not found");  
      Assert.IsNotNull(ModelStore, "Modeling store not found");  
    }  
    [AssemblyCleanup]  
    public static void RemoveTestSolution ()  
    {  
      // TODO: Remove copied test solution directory.  
    }  
  }  
}  
  
```  
  
 Если экземпляр <xref:EnvDTE.Project?displayProperty=fullName> представляет проект моделирования, можно привести его к и из <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.IModelingProject>.  
  
##  <a name="Opening"></a> Открытие схемы модели  
 Тесты или классы тестов, как правило, должны работать с открытой схемой. В следующем примере используется атрибут `[ClassInitialize]` , который выполняет этот метод раньше других методов в этом классе теста. Не забывайте, что атрибут [HostType("VS IDE")] также должен быть добавлен в каждый метод теста:  
  
```csharp  
//   
private IDiagram diagram;  
// This class contains unit tests:  
[TestClass]  
public class MyTestClass  
{  
  // Map filenames to open diagram files:  
  private static Dictionary<string, IDiagram> diagrams = new Dictionary<string, IDiagram>();  
  
  // This method will be called once for this test class:  
  [ClassInitialize]  
  [HostType("VS IDE")]  
  public static void TestClassInitialize(TestContext testContext)  
  {  
    // Open all the diagrams in the model:  
    foreach (ProjectItem item in (TestSetup.ModelingProject as Project).ProjectItems)  
    {  
      // Get the filename of the principal file (not the .layout subsidiary):  
      string fileName = item.FileNames[0];  
      // If this is a model diagram file, it can be cast to IDiagramContext:  
      IDiagramContext modelingItem = item as IDiagramContext;  
      if (modelingItem != null)  
      {  
        IDiagram diagram = modelingItem.CurrentDiagram;  
        if (diagram == null)  
        {  
          // Diagram is closed. Open it:  
          item.Open().Activate();  
          diagram = modelingItem.CurrentDiagram;  
        }  
        diagrams[fileName] = diagram;  
      }  
      // else item is not a model diagram.  
    }  
    Assert.IsTrue(diagrams.Count>0, "UML diagram not found");  
  }  
// Insert test methods here ...  
}  
  
```  
  
##  <a name="UiThread"></a> Выполнение изменений модели в потоке пользовательского интерфейса  
 Если ваши тесты (или методы в тестах) вносят изменения в хранилище моделей, их необходимо выполнять в потоке пользовательского интерфейса. В противном случае может быть создано исключение `AccessViolationException`. Заключите код метода теста в вызове в метод Invoke:  
  
```  
using System.Windows.Forms;  
using Microsoft.VSSDK.Tools.VsIdeTesting;  
 ...  
    [TestMethod]  
    [HostType("VS IDE")]  
    public void MyTest1()  
    {  
      // Store operations must run in the UI thread:  
      UIThreadInvoker.Invoke((System.Action)delegate()  
      {  
        SetupTestState(TestSetup.ModelStore, diagram);  
        ExecuteMethodUnderTest(TestSetup.ModelStore, diagram);  
      });  
    }  
```  
  
##  <a name="MEF"></a> Тестирование команд, жестов и других компонентов MEF  
 Компоненты MEF используют объявления свойств с атрибутом `[Import]` и значениями, задаваемыми их узлами. Обычно такие свойства включают IDiagramContext, SVsServiceProvider и ILinkedUndoContext. При тестировании метода, который использует любое из этих свойств, потребуется задать их значения до выполнения тестируемого метода. Например, если вы написали расширение команды наподобие следующего:  
  
```  
  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension]  
  class MyCommand : ICommandExtension  
  {  
    [Import] IDiagramContext context { get; set; }  
    [Import]   
Microsoft.VisualStudio.Shell.SVsServiceProvider  
serviceProvider {get;set;}  
    [Import] ILinkedUndoContext linkedUndoContext { get; set; }  
    public void Execute(IMenuCommand command)  
    {  
      DoCommand();  
    }  
    private void DoCommand()  
    {  
      IDiagram diagram = context.CurrentDiagram;  
      using (ILinkedUndoTransaction t = linkedUndoContext.BeginTransaction("go"))  
      { ... }}}  
  
```  
  
 Затем вы можете задать импортированные свойства следующим образом:  
  
```  
  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.ComponentModelHost;   
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
using Microsoft.VisualStudio.TestTools.UnitTesting;  
using Microsoft.VSSDK.Tools.VsIdeTesting;  
...  
    [TestMethod]   
    [HostType("VS IDE")]  
    public void Test1()  
    {  
      // Create an instance of the class under test:  
      MyCommand myCommand = new MyCommand();  
      // Get the components service:  
      IComponentModel components = VsIdeTestHostContext.ServiceProvider  
        .GetService(typeof(SComponentModel)) as IComponentModel;  
      // Set the imported properties of the instance under test:  
      // Extension requires "using System.ComponentModel.Composition;" :  
      components.DefaultCompositionService.SatisfyImportsOnce(myCommand);  
      // Call method(s) under test:  
      UIThreadInvoker.Invoke((System.Action)delegate()  
      {  
        myCommand.DoCommand();  
      });  
...}  
```  
  
 Если требуется протестировать метод, который принимает импортированное свойство в качестве параметра, свойство необходимо импортировать в класс теста и применить `SatisfyImportsOnce` к экземпляру теста. Пример:  
  
```  
  
using System.ComponentModel.Composition;  
...  
  [TestClass]  
  public class MyTestClass  
  {  
    [Import] ILinkedUndoContext linkedUndoContext { get; set; }  
  
    // Called before each test method:  
    [TestInitialize, HostType("VS IDE")]   
    public void TestInitializer()  
    {  
      IComponentModel components = VsIdeTestHostContext.ServiceProvider  
            .GetService(typeof(SComponentModel)) as IComponentModel;  
      // Extension requires "using System.ComponentModel.Composition;" :  
      components.DefaultCompositionService.SatisfyImportsOnce(this);  
    }  
    [TestMethod, HostType("VS IDE")]  
    public void Test2()  
    {   
     UIThreadInvoker.Invoke((System.Action)delegate()  
      {  
      // Pass context items to class under test:  
      Class1 item1 = new Class1(this.linkedUndoContext);  
      item1.Method1(); // Can use linkedUndoContext  
     });  
   }  
}  
  
```  
  
 В этом примере два атрибута каждого метода теста объединены в одну строку для удобства.  
  
## <a name="access-from-tests-to-private-methods-and-variables"></a>Доступ из тестов к закрытым методам и переменным  
 Иногда может потребоваться выполнить тестирование закрытого метода или проверить состояние закрытого поля до и после выполнения тестируемого метода. Это вызывает затруднения, так как тесты находятся в сборке, отдельной от тестируемых классов. Существует несколько рекомендуемых способов, включая перечисленные ниже.  
  
 Тестирование с помощью только открытых и внутренних элементов  
 Создайте тесты таким образом, чтобы они использовали только открытые (или внутренние) классы и члены. Это оптимальный способ. Ваши тесты будут продолжать работать даже в случае рефакторинга внутренней реализации тестируемой сборки. Применяя одни и те же тесты до и после внесения изменений, можно гарантировать, что изменения не повлияли на поведение сборки.  
  
 Для этого необходимо выполнить реструктуризацию кода. Например, может потребоваться выделить несколько методов в другой класс.  
  
 Если вы внимательно рассмотрите этот способ, вы обнаружите, что он позволяет упростить написание и изменение кода, а также сократить вероятность возникновения ошибок при внесении необходимых изменений.  
  
 Тестовым сборкам можно предоставить доступ к внутренним элементам, добавив в **Properties\AssemblyInfo.cs** тестируемого проекта следующий атрибут:  
  
```csharp  
[assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.  
```  
  
 Определение интерфейса теста  
 Определите интерфейс, который включает открытые члены тестируемого класса и дополнительные свойства и методы для закрытых членов, которые будут использоваться тестами. Добавьте этот интерфейс в тестируемый проект. Пример:  
  
```csharp  
internal interface MyClassTestInterface {  
  void PublicMethod1();  
  string PublicProperty1 { get; }  
  string privateField1_Accessor { get; }  
  int privateMethod1_Accessor (string p1);   
 }  
```  
  
 Добавьте методы в тестируемый класс, чтобы явно реализовать методы доступа. Отделите эти дополнительные методы от основного класса, записав их в определение разделяемого класса в отдельном файле. Пример:  
  
```csharp  
partial public class MyClass  
{  
  string MyClassTestInterface.privateField1_Accessor  
  { get { return privateField1; } }  
  int MyClassTestInterface.privateMethod1_Accessor (string p1)  
  { return privateMethod1(p1); }  
}  
  
```  
  
 Задайте для тестовой сборки разрешение использовать интерфейсы теста, добавив в тестируемую сборку следующий атрибут:  
  
```csharp  
[assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.  
```  
  
 В методах модульного теста используйте интерфейс теста. Пример:  
  
```csharp  
MyClassTestInterface testInstance = new MyClass();  
testInstance.PublicMethod1();  
Assert.AreEqual("hello", testInstance.privateField1_Accessor);  
```  
  
 Определение методов доступа с помощью отражения  
 Это наименее рекомендуемый способ. Старые версии [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] включали служебную программу, которая автоматически создавала метод доступа для каждого открытого метода. Опыт показывает, что хотя это и удобно, но приводит к тому, что модульные тесты становятся сильно привязанными к внутренней структуре приложения, для тестирования которого они используются. В результате приходится делать лишнюю работу в случае изменения требований или архитектуры, так как тесты нужно изменять вместе с реализацией. Кроме того, любые ошибочные допущения в проекте реализации также встраиваются в тесты, что не позволяет им находить ошибки.  
  
## <a name="see-also"></a>См. также  
 [Anatomy of a Unit Test](http://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144)  (Составляющие модульного теста)  
 [Определение команды меню на схеме моделирования](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [UML — быстрый ввод текста](http://code.msdn.microsoft.com/UML-Rapid-Entry-using-Text-0813ad8a)
