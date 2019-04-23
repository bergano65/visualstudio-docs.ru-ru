---
title: Использование членов Microsoft.VisualStudio.TestTools.UnitTesting в модульных тестах | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 0fa335fd-e442-448f-913f-25a19df90a93
caps.latest.revision: 8
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 37ca201f071d4cd9eda595a6fee6b95a23b4f05e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60095533"
---
# <a name="using-microsoftvisualstudiotesttoolsunittesting-members-in-unit-tests"></a>Использование членов Microsoft.VisualStudio.TestTools.UnitTesting в модульных тестах
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Платформа модульного тестирования поддерживает выполнение модульных тестов в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Используйте классы и элементы в пространстве имен <xref:Microsoft.VisualStudio.TestTools.UnitTesting> при написании модульных тестов. Они используются как при создании модульных тестов с нуля, так и при доработке тестов, созданных из проверяемого кода.

## <a name="groups-of-elements"></a>Группы элементов
 Для более четкого представления общих сведений о платформе модульного тестирования элементы пространства имен UnitTesting в этом разделе упорядочены по группам в зависимости от функциональности.

> [!NOTE]
> Элементы атрибутов, имена которых заканчиваются строкой "Attribute", можно использовать как со строкой "Attribute", так и без нее. Например, следующие два примера кода выполняют одну и ту же задачу:
>
>  `[TestClass()]`
>
>  `[TestClassAttribute()]`

### <a name="elements-used-for-data-driven-testing"></a>Элементы, используемые для управляемого данными тестирования
 Для настройки управляемых данными модульных тестов используются перечисленные ниже элементы. Дополнительные сведения см. в разделе [How To: Создание управляемого данными модульного теста](../test/how-to-create-a-data-driven-unit-test.md) и [Пошаговое руководство: С помощью файла конфигурации для определения источника данных](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>Атрибуты, используемые для установки порядка вызовов
 Кодовая точка, оформленная одним из перечисленных ниже атрибутов, вызывается в указанный момент времени. Дополнительные сведения см. в разделе [Составляющие модульного теста](http://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

### <a name="for-assemblies"></a>Для сборок
 Методы AssemblyInitialize и AssemblyCleanup вызываются сразу после загрузки сборки и непосредственно перед ее выгрузкой.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="for-classes"></a>Для классов
 Методы ClassInitialize и ClassCleanup вызываются сразу после загрузки класса и непосредственно перед его выгрузкой.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="for-test-methods"></a>Для методов теста

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Атрибуты, используемые для идентификации тестовых классов и методов
 Каждый тестовый класс должен иметь атрибут TestClass, а каждый тестовый метод — атрибут TestMethod. Дополнительные сведения см. в разделе [Составляющие модульного теста](http://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Классы Assert и связанные с ними исключения
 С помощью модульных тестов можно проверить поведение конкретного приложения, используя различные виды операторов, исключений и атрибутов Assert. Дополнительные сведения см. в разделе [Использование классов Assert](../test/using-the-assert-classes.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>

## <a name="the-testcontext-class"></a>Класс TestContext
 В окне свойств [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] приводятся указанные ниже атрибуты и связанные с ними значения для конкретного метода теста. Эти атрибуты не предназначены для доступа из кода модульного теста. Вместо этого они влияют на способ применения или выполнения модульного теста либо через интегрированную среду разработки [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], либо через модуль тестов [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Например, некоторые из этих атрибутов отображаются в качестве столбцов в окне диспетчера тестов и окне результатов теста, что позволяет использовать их для группировки и сортировки тестов и их результатов. Одним из таких атрибутов является TestPropertyAttribute, с помощью которого в модульные тесты добавляются произвольные метаданные. Например, его можно использовать для хранения имени тестового прохода данного теста, пометив модульный тест с помощью `[TestProperty("TestPass", "Accessibility")]`. Его также можно использовать для хранения индикатора типа теста: `[TestProperty("TestKind", "Localization")]`. Созданное с помощью этого атрибута свойство и присвоенное ему значение отображаются в окне свойств [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] под заголовком **Относится к тесту**.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DeploymentItemAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DescriptionAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.WorkItemAttribute>

## <a name="test-configuration-classes"></a>Классы конфигурации теста

- <xref:Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection>

## <a name="attributes-used-for-generating-reports"></a>Атрибуты, используемые для формирования отчетов
 В этом разделе приведены атрибуты, связывающие метод теста, к которому они применены, с сущностями в иерархии командного проекта [!INCLUDE[esprtfs](../includes/esprtfs-md.md)].

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>Классы, используемые с закрытыми методами доступа
 Как описывается в разделе [Использование Publicize для создания закрытого метода доступа](http://msdn.microsoft.com/2056c6a7-6672-42a7-8f53-fead33c56deb), вы можете создать модульный тест для закрытого метода. При этом создается класс закрытых методов доступа, являющийся экземпляром объекта класса PrivateObject. Класс PrivateObject является классом-оболочкой, использующим отражение в рамках процесса доступа через закрытые методы. Аналогичным является класс PrivateType, но вместо вызова закрытых методов экземпляра используется вызов закрытых статических методов.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>