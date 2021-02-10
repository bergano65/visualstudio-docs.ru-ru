---
title: Использование MSTest в модульных тестах
description: Сведения о платформе MSTest, которая поддерживает модульное тестирование в Visual Studio. Используйте такие классы и элементы для написания модульных тестов.
ms.custom: SEO-VS-2020
ms.date: 03/02/2018
ms.topic: reference
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 4eef06bb48730fba9ba1df145857d41323cbfdd7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946323"
---
# <a name="use-the-mstest-framework-in-unit-tests"></a>Использование платформы MSTest в модульных тестах

Платформа [MSTest](<xref:Microsoft.VisualStudio.TestTools.UnitTesting>) поддерживает модульное тестирование в Visual Studio. Используйте классы и элементы в пространстве имен <xref:Microsoft.VisualStudio.TestTools.UnitTesting> при написании модульных тестов. Их также можно использовать при оптимизации модульного теста, созданного на основе кода.

## <a name="framework-members"></a>Элементы платформы

Для более четкого описания платформы модульного тестирования в этом разделе элементы пространства имен <xref:Microsoft.VisualStudio.TestTools.UnitTesting> упорядочены по группам функций.

> [!NOTE]
> Элементы атрибутов, имена которых заканчиваются на "Attribute", можно использовать как с текстом "Attribute" в конце, так и без него. Например, следующие два примера кода выполняют одну и ту же задачу:
>
> `[TestClass()]`
>
> `[TestClassAttribute()]`

### <a name="members-used-for-data-driven-testing"></a>Элементы, используемые для управляемого данными тестирования

Для настройки управляемых данными модульных тестов используются перечисленные ниже элементы. Дополнительные сведения см. в статьях [Создание модульного теста, управляемого данными](../test/how-to-create-a-data-driven-unit-test.md) и [Использование файла конфигурации для определения источника данных](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>Атрибуты, используемые для упорядочивания вызовов

Кодовая точка, оформленная одним из перечисленных ниже атрибутов, вызывается в указанный момент времени. Дополнительные сведения см. в статье [Составляющие модульного теста](/previous-versions/ms182517(v=vs.110)).

### <a name="attributes-for-assemblies"></a>Атрибуты для сборок

Методы AssemblyInitialize и AssemblyCleanup вызываются сразу после загрузки сборки и непосредственно перед ее выгрузкой.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="attributes-for-classes"></a>Атрибуты для классов

Методы ClassInitialize и ClassCleanup вызываются сразу после загрузки класса и непосредственно перед его выгрузкой.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="attributes-for-test-methods"></a>Атрибуты для методов тестов

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Атрибуты для идентификации тестовых классов и методов

Каждый тестовый класс должен иметь атрибут `TestClass`, а каждый тестовый метод — атрибут `TestMethod`. Дополнительные сведения см. в статье [Составляющие модульного теста](/previous-versions/ms182517(v=vs.110)).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Классы Assert и связанные с ними исключения

С помощью модульных тестов можно проверить поведение конкретного приложения, используя различные виды утверждений, исключений и атрибутов. Дополнительные сведения см. в статье [Использование классов Assert](../test/using-the-assert-classes.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

## <a name="the-testcontext-class"></a>Класс TestContext

В окне свойств Visual Studio приводятся указанные ниже атрибуты и связанные с ними значения для конкретного метода теста. Эти атрибуты не предназначены для доступа из кода модульного теста. Но они влияют на способ применения или выполнения модульного теста с использованием интегрированной среды разработки либо модуля тестов Visual Studio. Например, некоторые из этих атрибутов отображаются в качестве столбцов в окне **диспетчера тестов** и окне **результатов тестов**. Это позволяет использовать их для группировки и сортировки тестов и их результатов. Одним из таких атрибутов является <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>, с помощью которого в модульные тесты добавляются произвольные метаданные. Например, его можно использовать для хранения имени тестового прохода данного теста, пометив модульный тест с помощью `[TestProperty("TestPass", "Accessibility")]`. Его также можно использовать для хранения индикатора типа теста с `[TestProperty("TestKind", "Localization")]`. Созданное с помощью этого атрибута свойство и присвоенное ему значение отображаются в окне **свойств** Visual Studio под заголовком **Относится к тесту**.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DeploymentItemAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DescriptionAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.WorkItemAttribute>

## <a name="test-configuration-classes"></a>Классы конфигурации теста

- [ObjectTypes](/previous-versions/visualstudio/visual-studio-2013/dd987428(v=vs.120))

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection>

## <a name="attributes-used-to-generate-reports"></a>Атрибуты для создания отчетов

В этом разделе приведены атрибуты, связывающие метод теста, к которому они применены, с сущностями в иерархии командного проекта Team Foundation Server.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>Классы, используемые с закрытыми методами доступа

Можно создать модульный тест для закрытого метода. При этом создается класс закрытых методов доступа, являющийся экземпляром объекта класса <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>. Класс <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> является классом-оболочкой, который использует отражение при осуществлении доступа через закрытые методы. Аналогичным является класс <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>, но вместо вызова закрытых методов экземпляра используется вызов закрытых статических методов.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>См. также раздел

- Справочная документация по <xref:Microsoft.VisualStudio.TestTools.UnitTesting>.