---
title: "Использование членов Microsoft.VisualStudio.TestTools.UnitTesting в модульных тестах | Документы Майкрософт"
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
ms.openlocfilehash: 251843d3e5a32ddedfe4f9081bd52330a457fe24
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="using-microsoftvisualstudiotesttoolsunittesting-members-in-unit-tests"></a>Использование членов Microsoft.VisualStudio.TestTools.UnitTesting в модульных тестах
Платформа модульного тестирования поддерживает выполнение модульных тестов в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. При написании кода модульных тестов используются классы и члены пространства имен Microsoft.VisualStudio.TestPlatform.UnitTestFramework>. Они используются как при создании модульных тестов с нуля, так и при доработке тестов, созданных из проверяемого кода.  
  
## <a name="groups-of-elements"></a>Группы элементов  
 Для более четкого представления общих сведений о платформе модульного тестирования элементы пространства имен UnitTesting в этом разделе упорядочены по группам в зависимости от функциональности.  
  
> [!NOTE]
>  Элементы атрибутов, имена которых заканчиваются строкой "Attribute", можно использовать как со строкой "Attribute", так и без нее. Например, следующие два примера кода выполняют одну и ту же задачу:  
>   
>  `[TestClass()]`  
>   
>  `[TestClassAttribute()]`  
  
### <a name="elements-used-for-data-driven-testing"></a>Элементы, используемые для управляемого данными тестирования  
 Для настройки управляемых данными модульных тестов используются перечисленные ниже элементы. Дополнительные сведения см. в разделах [Практическое руководство. Создание модульного теста, управляемого данными](../test/how-to-create-a-data-driven-unit-test.md) и [Пошаговое руководство. Использование файла конфигурации для определения источника данных](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataAccessMethod  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceAttribute 
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElement  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DataSourceElementCollection  
  
## <a name="attributes-used-to-establish-a-calling-order"></a>Атрибуты, используемые для установки порядка вызовов  
 Кодовая точка, оформленная одним из перечисленных ниже атрибутов, вызывается в указанный момент времени. Дополнительные сведения см. в разделе [Составляющие модульного теста](http://msdn.microsoft.com/en-us/a03d1ee7-9999-4e7c-85df-7d9073976144).  
  
### <a name="for-assemblies"></a>Для сборок  
 Методы AssemblyInitialize и AssemblyCleanup вызываются сразу после загрузки сборки и непосредственно перед ее выгрузкой.  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyInitializeAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssemblyCleanupAttribute  
  
### <a name="for-classes"></a>Для классов  
 Методы ClassInitialize и ClassCleanup вызываются сразу после загрузки класса и непосредственно перед его выгрузкой.  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassInitializeAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ClassCleanupAttribute  
  
### <a name="for-test-methods"></a>Для методов теста  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestInitializeAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestCleanupAttribute  
  
## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Атрибуты, используемые для идентификации тестовых классов и методов  
 Каждый тестовый класс должен иметь атрибут TestClass, а каждый тестовый метод — атрибут TestMethod. Дополнительные сведения см. в разделе [Составляющие модульного теста](http://msdn.microsoft.com/en-us/a03d1ee7-9999-4e7c-85df-7d9073976144).  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestClassAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestMethodAttribute  
  
## <a name="assert-classes-and-related-exceptions"></a>Классы Assert и связанные с ними исключения  
 С помощью модульных тестов можно проверить поведение конкретного приложения, используя различные виды операторов, исключений и атрибутов Assert. Дополнительные сведения см. в разделе [Использование классов Assert](../test/using-the-assert-classes.md).  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.Assert 
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CollectionAssert  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.StringAssert  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertFailedException  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.AssertInconclusiveException  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.UnitTestAssertException  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.ExpectedExceptionAttribute  
  
## <a name="the-testcontext-class"></a>Класс TestContext  
 В окне свойств [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] приводятся указанные ниже атрибуты и связанные с ними значения для конкретного метода теста. Эти атрибуты не предназначены для доступа из кода модульного теста. Вместо этого они влияют на способ применения или выполнения модульного теста либо через интегрированную среду разработки [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], либо через модуль тестов [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Например, некоторые из этих атрибутов отображаются в качестве столбцов в окне диспетчера тестов и окне результатов теста, что позволяет использовать их для группировки и сортировки тестов и их результатов. Одним из таких атрибутов является TestPropertyAttribute, с помощью которого в модульные тесты добавляются произвольные метаданные. Например, его можно использовать для хранения имени тестового прохода данного теста, пометив модульный тест с помощью `[TestProperty("TestPass", "Accessibility")]`. Его также можно использовать для хранения индикатора типа теста: `[TestProperty("TestKind", "Localization")]`. Созданное с помощью этого атрибута свойство и присвоенное ему значение отображаются в окне свойств [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] под заголовком **Относится к тесту**.  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.OwnerAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DeploymentItemAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.DescriptionAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.HostTypeAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.IgnoreAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PriorityAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestPropertyAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.WorkItemAttribute  
  
## <a name="test-configuration-classes"></a>Классы конфигурации теста  
  
-   Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.TestConfigurationSection  
  
## <a name="attributes-used-for-generating-reports"></a>Атрибуты, используемые для формирования отчетов  
 В этом разделе приведены атрибуты, связывающие метод теста, к которому они применены, с сущностями в иерархии командного проекта [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)].  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssIterationAttribute  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.CssProjectStructureAttribute  
  
## <a name="classes-used-with-private-accessors"></a>Классы, используемые с закрытыми методами доступа  
 Как описывается в разделе [Использование Publicize для создания закрытого метода доступа](http://msdn.microsoft.com/en-us/2056c6a7-6672-42a7-8f53-fead33c56deb), вы можете создать модульный тест для закрытого метода. При этом создается класс закрытых методов доступа, являющийся экземпляром объекта класса PrivateObject. Класс PrivateObject является классом-оболочкой, использующим отражение в рамках процесса доступа через закрытые методы. Аналогичным является класс PrivateType, но вместо вызова закрытых методов экземпляра используется вызов закрытых статических методов.  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateObject  
  
-   Microsoft.VisualStudio.TestPlatform.UnitTestFramework.PrivateType  
  
## <a name="see-also"></a>См. также  
 Microsoft.VisualStudio.TestPlatform.UnitTestFramework
