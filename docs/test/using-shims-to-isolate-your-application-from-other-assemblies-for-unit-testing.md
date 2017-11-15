---
title: "Использование оболочек совместимости для изоляции приложения от других сборок при модульном тестировании | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2a34de2-6527-4c21-8b93-2f268ee894b7
caps.latest.revision: "12"
ms.author: douge
manager: douge
ms.openlocfilehash: b95b4754af66c39d741b7df8a74a433ff812f834
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing"></a>Использование оболочек совместимости для изоляции приложения от других сборок при модульном тестировании
**Типы оболочек** — одна из двух технологий Microsoft Fakes Framework, используемых для простой изоляции тестируемых компонентов от окружения. Оболочки отвлекают вызовы к отдельным методам в коде, написанным в рамках теста. Множество методов возвращает различные результаты в зависимости от внешних условиях, но оболочка находится под контролем теста и может возвращать последовательные результаты при каждом вызове. Это позволяет создавать тесты намного проще.  
  
 Используйте оболочки, чтобы изолировать код из сборок, которые не входят в состав решения. Чтобы изолировать компоненты решения друг от друга, рекомендуется использовать заглушки.  
  
 Обзор и рекомендации по быстрому началу работы см. в разделе [Изоляция тестируемого кода с помощью Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)  
  
 **Requirements**  
  
-   Visual Studio Enterprise  
  
 См. видео (1 ч. 16 мин.): [Тестирование нетестируемого кода с помощью Fakes в Visual Studio 2012](http://go.microsoft.com/fwlink/?LinkId=261837)  
  
## <a name="in-this-topic"></a>Содержание раздела  
 Ниже перечислены темы, рассматриваемые в этом разделе.  
  
 [Пример. Ошибка 2000 года](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Example__The_Y2K_bug)  
  
 [Использование оболочек](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Fakes_requirements)  
  
-   [Добавление сборки Fakes](#AddFakes)  
  
-   [Использование ShimsContext](#ShimsContext)  
  
-   [Создание тестов с оболочками](#WriteTests)  
  
 [Оболочки для методов различных типов](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Shim_basics)  
  
-   [Статические методы](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Static_methods)  
  
-   [Методы экземпляра (для всех экземпляров)](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Instance_methods__for_all_instances_)  
  
-   [Методы экземпляра (для одного экземпляра)](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Instance_methods__for_one_instance_)  
  
-   [Конструкторы](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Constructors)  
  
-   [Базовые члены](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Base_members)  
  
-   [Статические конструкторы](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Static_constructors)  
  
-   [Методы завершения](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Finalizers)  
  
-   [Закрытые методы](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Private_methods)  
  
-   [Привязка интерфейсов](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Binding_interfaces)  
  
 [Изменение поведения по умолчанию](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Changing_the_default_behavior)  
  
 [Обнаружение событий доступа к среде](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Detecting_environment_accesses)  
  
 [Параллелизм](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Concurrency)  
  
 [Вызов исходного метода из метода оболочки совместимости](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Calling_the_original_method_from_the_shim_method)  
  
 [Ограничения](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md#BKMK_Limitations)  
  
##  <a name="BKMK_Example__The_Y2K_bug"></a> Пример. Ошибка 2000 года  
 Рассмотрим метод, который создает исключение 1 января 2000 г.  
  
```csharp  
// code under test  
public static class Y2KChecker {  
    public static void Check() {  
        if (DateTime.Now == new DateTime(2000, 1, 1))  
            throw new ApplicationException("y2kbug!");  
    }  
}  
  
```  
  
 Тестирование этого метода является особенно проблематичным, поскольку программа зависит от `DateTime.Now`, зависимого от часов компьютера и среды, недетерминированного метода. Кроме того, `DateTime.Now` является статическим свойством, поэтому здесь нельзя использовать тип заглушки. Эта проблема является признаком проблемы изоляции в модульных тестах: программы, которые непосредственно вызывают API базы данных, взаимодействуют с веб-службами и т. д., трудно тестировать с помощью модульных тестов, так как их логика зависит от среды.  
  
 В этом случае необходимо использовать типы оболочек совместимости. Типы оболочек совместимости обеспечивают механизм использования любым методом .NET определяемого пользователем делегата. Типы оболочек программно создаются генератором Fakes и используют делегаты, которые мы называем типами оболочек совместимости, для указания новых реализаций метода.  
  
 В следующем примере теста показано, как использовать тип оболочки совместимости `ShimDateTime` для предоставления настраиваемой реализации метода DateTime.Now.  
  
```csharp  
//unit test code  
// create a ShimsContext cleans up shims   
using (ShimsContext.Create()  
    // hook delegate to the shim method to redirect DateTime.Now  
    // to return January 1st of 2000  
    ShimDateTime.NowGet = () => new DateTime(2000, 1, 1);  
    Y2KChecker.Check();  
}  
  
```  
  
##  <a name="BKMK_Fakes_requirements"></a> Использование оболочек  
  
###  <a name="AddFakes"></a> Добавление сборок Fakes  
  
1.  В обозревателе решений разверните список **Ссылки** проекта модульного теста.  
  
    -   При работе в Visual Basic необходимо выбрать **Показать все файлы** на панели инструментов обозревателя решений, чтобы просмотреть список "Ссылки".  
  
2.  Выделите сборку, которая содержит определения классов, для которых необходимо создать оболочки. Например, если требуется создать оболочку для DateTime, выберите System.dll  
  
3.  В контекстном меню щелкните **Добавить сборку имитаций**.  
  
###  <a name="ShimsContext"></a> Использование ShimsContext  
 При использовании типов оболочек в среде модульного тестирования необходимо заключить код теста в контекст `ShimsContext` для управления временем существования оболочек совместимости. Если это не требуется, оболочки будут существовать до завершения работы домена приложения. Самый простой способ создания `ShimsContext` — использование статического метода `Create()`, как показано в следующем коде.  
  
```csharp  
//unit test code  
[Test]  
public void Y2kCheckerTest() {  
  using(ShimsContext.Create()) {  
    ...  
  } // clear all shims  
}  
  
```  
  
 Очень важно правильно ликвидировать каждый контекст оболочки. Как правило, следует всегда вызывать `ShimsContext.Create` внутри оператора `using`, чтобы гарантировать правильный сброс зарегистрированных оболочек. Например, можно зарегистрировать оболочку для метода теста, заменяющего метод `DateTime.Now` делегатом, который всегда возвращает 1 января 2000 г. Если вы забудете сбросить зарегистрированную оболочку в методе теста, остальная часть тестового запуска всегда будет возвращать в качестве значения DateTime.Now 1 января 2000 г. Это может быть неожиданно и неудобно.  
  
###  <a name="WriteShims"></a> Создание теста с оболочками  
 В коде теста вставьте *обход* для метода, который требуется имитировать. Пример:  
  
```csharp  
[TestClass]  
public class TestClass1  
{   
        [TestMethod]  
        public void TestCurrentYear()  
        {  
            int fixedYear = 2000;  
  
            using (ShimsContext.Create())  
            {  
              // Arrange:  
                // Detour DateTime.Now to return a fixed date:  
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
  
 Имена классов оболочки создаются путем добавления префикса `Fakes.Shim` к имени исходного типа.  
  
 Оболочки работают путем вставки *обходов* в код тестируемого приложения. Где бы ни возникал вызов исходного метода, система Fakes выполняет обход, чтобы вместо вызова настоящего метода происходил вызов кода оболочки.  
  
 Обратите внимание, что обходы создаются и удаляются во время выполнения. Всегда следует создавать обходы в течение существования `ShimsContext`. После его удаления все оболочки, созданные во время его активности, удаляются. Лучшего всего сделать это внутри оператора `using`.  
  
 Можно увидеть ошибку сборки, утверждающую, что пространство имен Fakes не существует. Иногда эта ошибка появляется, когда есть другие ошибки компиляции. Устраните остальные ошибки, и она исчезнет.  
  
##  <a name="BKMK_Shim_basics"></a> Оболочки для методов различных типов  
 Типы оболочки позволяют заменить любой метод .NET, включая статические методы или невиртуальные методы собственными делегатами.  
  
###  <a name="BKMK_Static_methods"></a> Статические методы  
 Свойства для присоединения оболочек совместимости к статическим методам помещаются в тип оболочки. Каждое свойство имеет только метод задания, который можно использовать для присоединения делегата к целевому методу. Например, имеется класс `MyClass` со статическим методом `MyMethod`.  
  
```csharp  
//code under test  
public static class MyClass {  
    public static int MyMethod() {  
        ...  
    }  
}  
```  
  
 Мы можем присоединить оболочку к методу `MyMethod`, который всегда возвращает значение 5.  
  
```csharp  
// unit test code  
ShimMyClass.MyMethod = () =>5;  
```  
  
###  <a name="BKMK_Instance_methods__for_all_instances_"></a> Методы экземпляра (для всех экземпляров)  
 Аналогично статическим методам для методов экземпляра можно создать оболочки для всех экземпляров. Свойства для присоединения этих оболочек помещаются во вложенный тип с именем AllInstances, чтобы избежать путаницы. Например, имеется класс `MyClass` с методом экземпляра `MyMethod`.  
  
```csharp  
// code under test  
public class MyClass {  
    public int MyMethod() {  
        ...  
    }  
}  
```  
  
 Можно присоединить оболочку к `MyMethod`, которая всегда возвращает 5, независимо от экземпляра:  
  
```csharp  
// unit test code  
ShimMyClass.AllInstances.MyMethod = () => 5;  
```  
  
 Структура созданного типа ShimMyClass похожа на следующий код.  
  
```csharp  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass> {  
    public static class AllInstances {  
        public static Func<MyClass, int>MyMethod {  
            set {  
                ...  
            }  
        }  
    }  
}  
```  
  
 Обратите внимание, что Fakes в этом случае передает экземпляр среды выполнения в качестве первого аргумента делегата.  
  
###  <a name="BKMK_Instance_methods__for_one_instance_"></a> Методы экземпляра (для одного экземпляра)  
 Для методов экземпляра можно также создать оболочки совместимости, используя разные делегаты в зависимости от получателя вызова. Это позволяет задать для одного метода экземпляра разные варианты поведения в зависимости от экземпляра типа. Свойства для настройки этих оболочек являются методами экземпляра самого типа оболочки. Каждый экземпляр типа оболочки также связан с необработанным экземпляром типа с оболочкой совместимости.  
  
 Например, имеется класс `MyClass` с методом экземпляра `MyMethod`.  
  
```csharp  
// code under test  
public class MyClass {  
    public int MyMethod() {  
        ...  
    }  
}  
```  
  
 Мы можем настроить два типа оболочки MyMethod таким образом, что первый тип будет всегда возвращать значение 5, а второй — 10.  
  
```csharp  
// unit test code  
var myClass1 = new ShimMyClass()  
{  
    MyMethod = () => 5  
};  
var myClass2 = new ShimMyClass { MyMethod = () => 10 };  
```  
  
 Структура созданного типа ShimMyClass похожа на следующий код.  
  
```csharp  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass> {  
    public Func<int> MyMethod {  
        set {  
            ...  
        }  
    }  
    public MyClass Instance {  
        get {  
            ...  
        }  
    }  
}  
```  
  
 Доступ к фактическому экземпляру типа с оболочкой совместимости можно получить с помощью свойства Instance.  
  
```csharp  
// unit test code  
var shim = new ShimMyClass();  
var instance = shim.Instance;  
```  
  
 Тип оболочки совместимости также имеет неявное преобразование в тип с оболочкой, поэтому, как правило, тип оболочки можно просто использовать как есть.  
  
```csharp  
// unit test code  
var shim = new ShimMyClass();  
MyClass instance = shim; // implicit cast retrieves the runtime  
                         // instance  
```  
  
###  <a name="BKMK_Constructors"></a> Конструкторы  
 Для конструкторов также можно создать оболочки совместимости для присоединения типов оболочки к будущим объектам. Каждый конструктор предоставляется как статический метод конструктора в типе оболочки совместимости. Например, имеется класс `MyClass` с конструктором, принимающим целое число.  
  
```csharp  
// code under test  
public class MyClass {  
    public MyClass(int value) {  
        this.Value = value;  
    }  
    ...  
}  
```  
  
 Мы настраиваем тип оболочки совместимости конструктора так, чтобы каждый будущий экземпляр возвращал -5, если вызывается метод получения значения, независимо от значения в конструкторе.  
  
```csharp  
// unit test code  
ShimMyClass.ConstructorInt32 = (@this, value) => {  
    var shim = new ShimMyClass(@this) {  
        ValueGet = () => -5  
    };  
};  
```  
  
 Обратите внимание, что каждый тип оболочки предоставляет два конструктора. Конструктор по умолчанию следует использовать при необходимости создания нового экземпляра, тогда как конструктор, принимающий экземпляр с оболочкой в качестве аргумента, следует использовать только в оболочках совместимости конструктора.  
  
```csharp  
// unit test code  
public ShimMyClass() { }  
public ShimMyClass(MyClass instance) : base(instance) { }  
```  
  
 Структура созданного типа ShimMyClass похожа на следующий код.  
  
```csharp  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass>  
{  
    public static Action<MyClass, int> ConstructorInt32 {  
        set {  
            ...  
        }  
    }  
  
    public ShimMyClass() { }  
    public ShimMyClass(MyClass instance) : base(instance) { }  
    ...  
}  
```  
  
###  <a name="BKMK_Base_members"></a> Базовые члены  
 Доступ к свойствам оболочки совместимости базовых членов может осуществляться путем создания оболочки для базового типа и передачи дочернего экземпляра в качестве параметра в конструктор базового класса оболочки.  
  
 Например, имеется класс `MyBase` с методом экземпляра `MyMethod` и подтипом `MyChild`.  
  
```csharp  
public abstract class MyBase {  
    public int MyMethod() {  
        ...  
    }  
}  
  
public class MyChild : MyBase {  
}  
  
```  
  
 Мы можем настроить оболочку совместимости `MyBase`, создав новую оболочку `ShimMyBase`.  
  
```csharp  
// unit test code  
var child = new ShimMyChild();  
new ShimMyBase(child) { MyMethod = () => 5 };  
```  
  
 Обратите внимание, что дочерний тип оболочки неявно преобразуется в дочерний экземпляр при передаче в качестве параметра в конструктор базовой оболочки совместимости.  
  
 Структура созданного типа ShimMyChild и ShimMyBase похожа на следующий код.  
  
```csharp  
// Fakes generated code  
public class ShimMyChild : ShimBase<MyChild> {  
    public ShimMyChild() { }  
    public ShimMyChild(Child child)  
        : base(child) { }  
}  
public class ShimMyBase : ShimBase<MyBase> {  
    public ShimMyBase(Base target) { }  
    public Func<int> MyMethod  
    { set { ... } }  
}  
```  
  
###  <a name="BKMK_Static_constructors"></a> Статические конструкторы  
 Типы оболочек совместимости предоставляют статический метод `StaticConstructor`, чтобы создать оболочку для статического конструктора типа. Поскольку статические конструкторы выполняются только один раз, необходимо убедиться, что оболочка настроена перед получением доступа к любому члену типа.  
  
###  <a name="BKMK_Finalizers"></a> Методы завершения  
 Методы завершения не поддерживаются в Fakes.  
  
###  <a name="BKMK_Private_methods"></a> Закрытые методы  
 Генератор кода Fakes создает свойства оболочки для закрытых методов, которые имеют только видимые типы в сигнатуре, например видимые типы параметров и типы возвращаемого значения.  
  
###  <a name="BKMK_Binding_interfaces"></a> Привязка интерфейсов  
 Когда тип с оболочкой совместимости реализует интерфейс, генератор кода создает метод, позволяющий ему привязать все члены из этого интерфейса за один раз.  
  
 Например, имеется класс `MyClass`, реализующий интерфейс `IEnumerable<int>`.  
  
```csharp  
public class MyClass : IEnumerable<int> {  
    public IEnumerator<int> GetEnumerator() {  
        ...  
    }  
    ...  
}  
  
```  
  
 Мы можем создать оболочки для реализаций `IEnumerable<int>` в MyClass путем вызова метода привязки.  
  
```csharp  
// unit test code  
var shimMyClass = new ShimMyClass();  
shimMyClass.Bind(new List<int> { 1, 2, 3 });  
  
```  
  
 Структура созданного типа ShimMyClass похожа на следующий код.  
  
```csharp  
// Fakes generated code  
public class ShimMyClass : ShimBase<MyClass> {  
    public ShimMyClass Bind(IEnumerable<int> target) {  
        ...  
    }  
}  
  
```  
  
##  <a name="BKMK_Changing_the_default_behavior"></a> Изменение поведения по умолчанию  
 Каждый созданный тип оболочки содержит экземпляр интерфейса `IShimBehavior` через свойство `ShimBase<T>.InstanceBehavior`. Это поведение используется, когда клиент вызывает член экземпляра, для которого оболочка не создана явно.  
  
 Если поведение не задано явно, будет использоваться экземпляр, возвращаемый статическим свойством `ShimsBehaviors.Current`. По умолчанию это свойство возвращает поведение, вызывающее исключение `NotImplementedException`.  
  
 Это поведение можно изменить в любой момент, задав свойство `InstanceBehavior` для любого экземпляра оболочки совместимости. Например, в следующем фрагменте кода изменяется поведение оболочки, которое ничего не делает или возвращает значение по умолчанию возвращаемого типа, то есть default(T).  
  
```csharp  
// unit test code  
var shim = new ShimMyClass();  
//return default(T) or do nothing  
shim.InstanceBehavior = ShimsBehaviors.DefaultValue;  
  
```  
  
 Поведение также можно изменить глобально для всех экземпляров с оболочками совместимости, для которых свойство `InstanceBehavior` не было задано явно, путем задания статического свойства `ShimsBehaviors.Current`.  
  
```csharp  
// unit test code  
// change default shim for all shim instances  
// where the behavior has not been set  
ShimsBehaviors.Current =   
    ShimsBehaviors.DefaultValue;  
  
```  
  
##  <a name="BKMK_Detecting_environment_accesses"></a> Обнаружение событий доступа к среде  
 Можно назначить поведение всем членам (включая статические методы) определенного типа, назначив поведение `ShimsBehaviors.NotImplemented` статическому свойству `Behavior` соответствующего типа оболочки.  
  
```csharp  
// unit test code  
// assigning the not implemented behavior  
ShimMyClass.Behavior = ShimsBehaviors.NotImplemented;  
// shorthand  
ShimMyClass.BehaveAsNotImplemented();  
  
```  
  
##  <a name="BKMK_Concurrency"></a> Параллелизм  
 Типы оболочек совместимости применяются ко всем потокам в домене приложения, и к ним не применяется сходство потоков. Это важный аспект, если вы планируете использовать средства выполнения тестов, которые поддерживают параллельность: тесты, включающие типы оболочек, нельзя запускать одновременно. Это свойство не применяется средой выполнения Fakes принудительно.  
  
##  <a name="BKMK_Calling_the_original_method_from_the_shim_method"></a> Вызов исходного метода из метода оболочки совместимости  
 Предположим, мы хотим фактически записать текст в файловую систему после проверки имени файла, переданного в метод. В этом случае нам потребуется вызвать исходный метод в середине метода оболочки.  
  
 Первый подход для решения этой проблемы — заключить вызов исходного метода в оболочку с помощью делегата и `ShimsContext.ExecuteWithoutShims()`, как показано в следующем примере кода.  
  
```csharp  
// unit test code  
ShimFile.WriteAllTextStringString = (fileName, content) => {  
  ShimsContext.ExecuteWithoutShims(() => {  
  
      Console.WriteLine("enter");  
      File.WriteAllText(fileName, content);  
      Console.WriteLine("leave");  
  });  
};  
  
```  
  
 Другой подход заключается в задании для оболочки совместимости значения null, вызове исходного метода и восстановлении оболочки.  
  
```csharp  
// unit test code  
ShimsDelegates.Action<string, string> shim = null;  
shim = (fileName, content) => {  
  try {  
    Console.WriteLine("enter");  
    // remove shim in order to call original method  
    ShimFile.WriteAllTextStringString = null;  
    File.WriteAllText(fileName, content);  
  }  
  finally  
  {  
    // restore shim  
    ShimFile.WriteAllTextStringString = shim;  
    Console.WriteLine("leave");  
  }  
};  
// initialize the shim  
ShimFile.WriteAllTextStringString = shim;  
  
```  
  
##  <a name="BKMK_Limitations"></a> Ограничения  
 Оболочки совместимости нельзя использовать для всех типов из библиотеки базовых классов .NET **mscorlib** и **System**.  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
### <a name="guidance"></a>Руководство  
 [Тестирование непрерывной доставки с Visual Studio 2012 — глава 2. Модульное тестирование. Внутреннее тестирование](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>См. также  
 [Изоляция тестируемого кода с помощью Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)   
 [Блог Питера Провоста (Peter Provost): оболочки Visual Studio 2012](http://www.peterprovost.org/blog/2012/04/25/visual-studio-11-fakes-part-2)   
 [Видео (1 ч. 16 мин.): тестирование нетестируемого кода с помощью Fakes в Visual Studio 2012](http://go.microsoft.com/fwlink/?LinkId=261837)
