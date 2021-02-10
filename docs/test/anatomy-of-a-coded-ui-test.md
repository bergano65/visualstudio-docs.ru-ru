---
title: Составляющие закодированного теста пользовательского интерфейса
description: Сведения о файлах, которые добавляются в ваше решение закодированного теста пользовательского интерфейса при создании такого теста.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 65b55c79dd39b5e8393d22542a2334d84b191293
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933080"
---
# <a name="anatomy-of-a-coded-ui-test"></a>Составляющие закодированного теста пользовательского интерфейса

При создании закодированного теста пользовательского интерфейса в проекте закодированного теста пользовательского интерфейса к решению добавляются несколько файлов. Эти файлы описываются в данной статье.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="contents-of-a-coded-ui-test"></a>Содержимое закодированного теста пользовательского интерфейса

При создании закодированного теста пользовательского интерфейса **построитель закодированных тестов пользовательского интерфейса** создает карту тестируемого пользовательского интерфейса, а также методы тестов, параметры и утверждения для всех тестов. Он также создает файл класса для каждого теста.

|Файл|Содержимое|Редактируемый?|
|-|-|-|
|[UIMap.Designer.cs](#UIMapDesignerFile)|[Раздел объявлений](#UIMapDesignerFile)<br /><br /> [Класс UIMap](#UIMapClass) (разделяемый, автоматически создаваемый)<br /><br /> [Методы](#UIMapMethods)<br /><br /> [Свойства](#UIMapProperties)|нет|
|[UIMap.cs](#UIMapCS)|[Класс UIMap](#UIMapCS) (разделяемый)|Да|
|[CodedUITest1.cs](#CodedUITestCS)|[Класс CodedUITest1](#CodedUITestCS)<br /><br /> [Методы](#CodedUITestMethods)<br /><br /> [Свойства](#CodedUITestProperties)|Да|
|[UIMap.uitest](#UIMapuitest)|XML-карта пользовательского интерфейса для теста.|нет|

### <a name="uimapdesignercs"></a><a name="UIMapDesignerFile"></a> UIMap.Designer.cs
Этот файл содержит код, который создается автоматически **построителем закодированных тестов пользовательского интерфейса** при создании теста. Этот файл создается заново при каждом изменении теста, поэтому вы не можете добавлять в него код или изменять его.

#### <a name="declarations-section"></a>Раздел объявлений
Этот раздел содержит следующие объявления для пользовательского интерфейса Windows.

```csharp
using System;
using System.CodeDom.Compiler;
using System.Collections.Generic;
using System.Drawing;
using System.Text.RegularExpressions;
using System.Windows.Input;
using Microsoft.VisualStudio.TestTools.UITest.Extension;
using Microsoft.VisualStudio.TestTools.UITesting;
using Microsoft.VisualStudio.TestTools.UITesting.WinControls;
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Keyboard = Microsoft.VisualStudio.TestTools.UITesting.Keyboard;
using Mouse = Microsoft.VisualStudio.TestTools.UITesting.Mouse;
using MouseButtons = System.Windows.Forms.MouseButtons;
```

Пространство имен <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls> включается для пользовательского интерфейса Windows. Для пользовательского интерфейса веб-страниц будет использоваться пространство имен <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>; для пользовательского интерфейса Windows Presentation Foundation будет использоваться пространство имен <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>.

#### <a name="uimap-class"></a><a name="UIMapClass"></a> Класс UIMap
Следующий раздел файла — это класс [UIMap](/previous-versions/dd580454(v=vs.140)).

```csharp
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]
public partial class UIMap
```

Код класса начинается с атрибута <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>, который применяется к этому классу, объявленному как разделяемый класс. Обратите внимание, что этот атрибут также применяется ко всем классам в данном файле. Дополнительный код для этого класса может содержаться в другом файле *UIMap.cs*, который рассматривается ниже.

Созданный класс `UIMap` содержит код для каждого метода, указанного при записи теста.

```csharp
public void LaunchCalculator()
public void AddItems()
public void VerifyTotal()
public void CleanUp()
```

Эта часть класса [UIMap](/previous-versions/dd580454(v=vs.140)) также включает созданный код для каждого свойства, необходимого методам.

```csharp
public virtual LaunchCalculatorParams LaunchCalculatorParams
public virtual AddItemsParams AddItemsParams
public virtual VerifyTotalExpectedValues VerifyTotalExpectedValues
public virtual CalculateItemsParams CalculateItemsParams
public virtual VerifyMathAppTotalExpectedValues
    VerifyMathAppTotalExpectedValues
public UIStartMenuWindow UIStartMenuWindow
public UIRunWindow UIRunWindow
public UICalculatorWindow UICalculatorWindow
public UIStartWindow UIStartWindow
public UIMathApplicationWindow UIMathApplicationWindow
```

##### <a name="uimap-methods"></a><a name="UIMapMethods"></a> Методы UIMap
Каждый метод имеет структуру, напоминающую метод `AddItems()`. Эта структура более подробно объясняется в коде, который для большей ясности представлен с использованием разрывов строк.

```csharp
/// <summary>
/// AddItems - Use 'AddItemsParams' to pass parameters into this method.
/// </summary>
public void AddItems()
{
    #region Variable Declarations
    WinControl uICalculatorDialog =
        this.UICalculatorWindow.UICalculatorDialog;
    WinEdit uIItemEdit =
        this.UICalculatorWindow.UIItemWindow.UIItemEdit;
    #endregion

    // Type '{NumPad7}' in 'Calculator' Dialog
    Keyboard.SendKeys(uICalculatorDialog,
        this.AddItemsParams.UICalculatorDialogSendKeys,
        ModifierKeys.None);

    // Type '{Add}{NumPad2}{Enter}' in 'Unknown Name' text box
    Keyboard.SendKeys(uIItemEdit,
        this.AddItemsParams.UIItemEditSendKeys,
        ModifierKeys.None);
}
```

В сводном комментарии для каждого определения метода указывается, какой класс должен использоваться для значений параметров для этого метода. В данном случае это класс `AddItemsParams`, который определяется далее в файле *UIMap.cs*, и это также тип значения, возвращаемый свойством `AddItemsParams`.

В верхней части кода метода имеется область `Variable Declarations`, определяющая локальные переменные для объектов пользовательского интерфейса, которые используются методом.

В данном методе доступ к свойствам `UIItemWindow` и `UIItemEdit` осуществляется с помощью класса `UICalculatorWindow`, который определяется позднее в файле *UIMap.cs*.

Далее идут строки, которые отправляют текст с клавиатуры в приложение «Калькулятор» с помощью свойств объекта `AddItemsParams`.

Метод `VerifyTotal()` имеет похожую структуру и включает следующий код утверждения:

```csharp
// Verify that 'Unknown Name' text box's property 'Text' equals '9. '
Assert.AreEqual(
    this.VerifyTotalExpectedValues.UIItemEditText,
    uIItemEdit.Text);
```

Имя текстового поля указано как неизвестное, поскольку разработчик приложения «Калькулятор Windows» не предоставил общедоступное имя для элемента управления. Метод <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName> завершается неудачно, если фактическое значение не равно ожидаемому значению, что приведет к сбою теста. Также обратите внимание, что ожидаемое значение содержит десятичную точку, за которой следует пробел. Если вам когда-нибудь понадобится изменить функциональные возможности данного теста, необходимо будет предусмотреть эту десятичную точку и пробел.

##### <a name="uimap-properties"></a><a name="UIMapProperties"></a> Свойства UIMap
Код для каждого свойства также довольно стандартный во всем классе. Следующий код для свойства `AddItemsParams` используется в методе `AddItems()`.

```csharp
public virtual AddItemsParams AddItemsParams
{
    get
    {
        if ((this.mAddItemsParams == null))
        {
            this.mAddItemsParams = new AddItemsParams();
        }
        return this.mAddItemsParams;
    }
}
```

Обратите внимание, что это свойство использует закрытую локальную переменную с именем `mAddItemsParams` для хранения значения перед его возвратом. Имя свойства и имя класса для возвращаемого объекта одинаковы. Этот класс определяется позднее в файле *UIMap.cs*.

Все классы, возвращаемые свойством, имеют аналогичную структуру. Далее следует класс `AddItemsParams`:

```csharp
/// <summary>
/// Parameters to be passed into 'AddItems'
/// </summary>
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]
public class AddItemsParams
{
    #region Fields
    /// <summary>
    /// Type '{NumPad7}' in 'Calculator' Dialog
    /// </summary>
    public string UICalculatorDialogSendKeys = "{NumPad7}";

    /// <summary>
    /// Type '{Add}{NumPad2}{Enter}' in 'Unknown Name' text box
    /// </summary>
    public string UIItemEditSendKeys = "{Add}{NumPad2}{Enter}";
    #endregion
}
```

Как и все классы в файле *UIMap.cs*, данный класс начинается с атрибута <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>. В этом небольшом классе имеется область `Fields`, определяющая строки, которые должны использоваться в качестве параметров для метода <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName>, используемого в рассмотренном выше методе `UIMap.AddItems()`. Вы можете написать код для замены значений в этих строковых полях до вызова метода, в котором используются эти параметры.

### <a name="uimapcs"></a><a name="UIMapCS"></a> UIMap.cs
По умолчанию этот файл содержит разделяемый класс `UIMap`, в котором отсутствуют методы и свойства.

#### <a name="uimap-class"></a>Класс UIMap
В этом классе вы можете создать пользовательский код для расширения функциональных возможностей класса [UIMap](/previous-versions/dd580454(v=vs.140)). Код, созданный в этом файле, не перезаписывается **построителем закодированных тестов пользовательского интерфейса** при каждом изменении теста.

Все части [UIMap](/previous-versions/dd580454(v=vs.140)) могут использовать методы и свойства из других частей класса [UIMap](/previous-versions/dd580454(v=vs.140)).

### <a name="codeduitest1cs"></a><a name="CodedUITestCS"></a> CodedUITest1.cs
Этот файл создается **построителем закодированных тестов пользовательского интерфейса**, но не пересоздается при каждом изменении теста, поэтому вы можете изменять код в этом файле. Имя файла формируется из имени, указанного для теста при его создании.

#### <a name="codeduitest1-class"></a>Класс CodedUITest1

По умолчанию этот файл содержит определение только для одного класса.

```csharp
[CodedUITest]
public class CodedUITest1
```

К этому классу автоматически применяется атрибут [CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120)), который позволяет платформе тестирования распознать его как расширение тестирования. Также обратите внимание, что это не разделяемый класс. В этом файле содержится весь код класса.

##### <a name="codeduitest1-properties"></a><a name="CodedUITestProperties"></a> Свойства CodedUITest1

Данный класс содержит два свойства по умолчанию, которые находятся в нижней части файла. Не изменяйте их.

```csharp
/// <summary>
/// Gets or sets the test context which provides
/// information about and functionality for the current test run.
///</summary>
public TestContext TestContext
public UIMap UIMap
```

##### <a name="codeduitest1-methods"></a><a name="CodedUITestMethods"></a> Методы CodedUITest1
По умолчанию класс содержит только один метод.

```csharp
public void CodedUITestMethod1()
```

Этот метод вызывает каждый метод `UIMap`, указанный при записи теста, как описано в разделе [Класс UIMap](#UIMapClass).

Если область с заголовком `Additional test attributes` не закомментирована, то она содержит два дополнительных метода.

```csharp
// Use TestInitialize to run code before running each test
[TestInitialize()]
public void MyTestInitialize()
{
    // To generate code for this test, select "Generate Code for Coded
    // UI Test" from the shortcut menu and select one of the menu items.
    // For more information on generated code, see
    // http://go.microsoft.com/fwlink/?LinkId=179463

    // You could move this line from the CodedUITestMethod1() method
    this.UIMap.LaunchCalculator();
}

// Use TestCleanup to run code after each test has run
[TestCleanup()]
public void MyTestCleanup()
{
    // To generate code for this test, select "Generate Code for Coded
    // UI Test" from the shortcut menu and select one of the menu items.
    // For more information on generated code, see
    // http://go.microsoft.com/fwlink/?LinkId=179463

    // You could move this line from the CodedUITestMethod1() method
    this.UIMap.CloseCalculator();
}
```

Метод `MyTestInitialize()` имеет применяемый к нему атрибут <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>, который указывает платформе тестирования вызывать этот метод до всех остальных методов теста. Аналогично метод `MyTestCleanup()` имеет применяемый к нему атрибут <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>, который указывает платформе тестирования вызывать этот метод после вызова остальных методов теста. Использование этих методов является необязательным. Для данного теста метод `UIMap.LaunchCalculator()` может быть вызван из `MyTestInitialize()`, а метод `UIMap.CloseCalculator()` может быть вызван из `MyTestCleanup()` вместо `CodedUITest1Method1()`.

При добавлении в данный класс дополнительных методов с помощью [CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120)) платформа тестирования вызывает каждый метод в рамках этого теста.

### <a name="uimapuitest"></a><a name="UIMapuitest"></a> UIMap.uitest
Это XML-файл, представляющий структуру записанного закодированного теста пользовательского интерфейса и всех его частей. Сюда входят действия и классы, а также методы и свойства этих классов. Файл [UIMap.Designer.cs](#UIMapDesignerFile) содержит код, созданный построителем закодированных тестов пользовательского интерфейса для воспроизведения структуры теста, и обеспечивает подключение в платформе тестирования.

Файл *UIMap.uitest* невозможно редактировать напрямую. Однако можно использовать построитель закодированных тестов пользовательского интерфейса, который автоматически изменяет файлы *UIMap.uitest* и [*UIMap.Designer.cs*](#UIMapDesignerFile).

## <a name="see-also"></a>См. также раздел

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>
- <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName>
- [CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120))
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>
- [Использование автоматизации пользовательского интерфейса для тестирования кода](../test/use-ui-automation-to-test-your-code.md)
- [Создание закодированных тестов пользовательского интерфейса](../test/use-ui-automation-to-test-your-code.md)
- [Рекомендации по выполнению закодированных тестов пользовательского интерфейса](../test/best-practices-for-coded-ui-tests.md)
- [Тестирование крупного приложения с несколькими картами пользовательского интерфейса](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Поддерживаемые конфигурации и платформы для закодированных тестов пользовательского интерфейса и записей действий](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
