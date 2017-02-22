---
title: "Использование членов Microsoft.VisualStudio.TestTools.UnitTesting в модульных тестах | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0fa335fd-e442-448f-913f-25a19df90a93
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "mlearned"
manager: "douge"
---
# Использование членов Microsoft.VisualStudio.TestTools.UnitTesting в модульных тестах
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Платформа Unit Testing Framework поддерживает выполнение модульных тестов в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  При написании кода модульных тестов используются классы и члены пространства имен <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework>.  Они используются как при создании модульных тестов с нуля, так и при доработке тестов, созданных из проверяемого кода.  
  
## Группы элементов  
 Для более четкого представления общих сведений о платформе Unit Testing Framework элементы пространства имен "UnitTesting" в данном разделе упорядочены по группам в зависимости от функциональности.  
  
> [!NOTE]
>  Элементы атрибутов, имена которых заканчиваются строкой "Attribute", могут использоваться как со строкой "Attribute", так и без нее.  Например, следующие два примера кода выполняют одну и ту же задачу.  
>   
>  `[TestClass()]`  
>   
>  `[TestClassAttribute()]`  
  
### Элементы, используемые для управляемого данными тестирования  
 Для настройки управляемых данными модульных тестов используются следующие элементы.  Дополнительные сведения см. в разделах [Практическое руководство. Создание модульного теста, управляемого данными](../test/how-to-create-a-data-driven-unit-test.md) и [Пошаговое руководство. Использование файла конфигурации для определения источника данных](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataAccessMethod>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElement>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElementCollection>  
  
## Атрибуты, используемые для установки порядка вызовов  
 Кодовая точка, оформленная одним из следующих атрибутов, вызывается в указанный момент времени.  Для получения дополнительной информации см. [Составляющие модульного теста](http://msdn.microsoft.com/ru-ru/a03d1ee7-9999-4e7c-85df-7d9073976144).  
  
### Для сборок  
 Методы "AssemblyInitialize" и "AssemblyCleanup" вызываются сразу после загрузки сборки и непосредственно перед ее выгрузкой.  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyInitializeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyCleanupAttribute>  
  
### Для классов  
 Методы "ClassInitialize" и "ClassCleanup" вызываются сразу после загрузки класса и непосредственно перед его выгрузкой.  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassInitializeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassCleanupAttribute>  
  
### Для методов теста  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestInitializeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestCleanupAttribute>  
  
## Атрибуты, используемые для идентификации тестовых классов и методов  
 Каждый тестовый класс должен иметь атрибут "TestClass", каждый тестовый метод — атрибут "TestMethod".  Для получения дополнительной информации см. [Составляющие модульного теста](http://msdn.microsoft.com/ru-ru/a03d1ee7-9999-4e7c-85df-7d9073976144).  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestClassAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestMethodAttribute>  
  
## Классы "Assert" и связанные с ним исключения  
 С помощью модульных тестов можно проверить поведение конкретного приложения, используя различные вид операторов, исключений и атрибутов "Assert".  Для получения дополнительной информации см. [Использование классов Assert](../test/using-the-assert-classes.md).  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.Assert>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CollectionAssert>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.StringAssert>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertFailedException>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertInconclusiveException>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.UnitTestAssertException>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ExpectedExceptionAttribute>  
  
## Класс "TestContext"  
 В окне свойств [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] отображаются следующие атрибуты и связанные с ними значения для конкретного метода теста.  Эти атрибуты не предназначены для доступа из кода модульного теста.  Вместо этого они влияют на способ применения или выполнения модульного теста либо через интегрированную среду разработки [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], либо через обработчик тестов [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Например, некоторые из этих атрибутов появляются в качестве столбцов в окне диспетчера тестов и окне результатов теста, что позволяет использовать их для группировки и сортировки тестов и их результатов.  Одним из таких атрибутов является "TestPropertyAttribute", с помощью которого в модульные тесты добавляются произвольные метаданные.  Например, его можно использовать для хранения имени области действия пройденного теста, пометив модульный тест с помощью `[TestProperty("TestPass", "Accessibility")]`.  Или его можно использовать для хранения индикатора типа теста: `[TestProperty("TestKind", "Localization")]`.  Созданное с помощью этого атрибута свойство и присвоенное ему значение отобразятся в окне свойств [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] под заголовком **Сведения теста**.  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.OwnerAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DeploymentItemAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DescriptionAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.HostTypeAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.IgnoreAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PriorityAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestPropertyAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.WorkItemAttribute>  
  
## Классы конфигурации теста  
  
-   <xref:Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestConfigurationSection>  
  
## Атрибуты, используемые для формирования отчетов  
 В этом разделе описаны атрибуты, связывающие метод теста, к которому они применены, с сущностями в иерархии командного проекта [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)].  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssIterationAttribute>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssProjectStructureAttribute>  
  
## Классы, использующие закрытые методы доступа  
 Как описывается в разделе [Using Publicize to Create a Private Accessor](http://msdn.microsoft.com/ru-ru/2056c6a7-6672-42a7-8f53-fead33c56deb), вы можете создать модульный тест для закрытого метода.  При этом создается класс закрытых методов доступа, являющийся экземпляром объекта класса "PrivateObject".  Класс "PrivateObject" является классом\-оболочкой, использующим отражение в рамках процесса доступа через закрытые методы.  Аналогичным является класс "PrivateType", но вместо вызова закрытых методов экземпляра используется вызов закрытых статических методов.  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateObject>  
  
-   <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateType>  
  
## См. также  
 <xref:Microsoft.VisualStudio.TestPlatform.UnitTestFramework>