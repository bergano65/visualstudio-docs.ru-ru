---
title: Обновление настроек ленты в проектах Office, перенесенных на .NET Framework 4, 4,5
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c7d7ab5755f592e57e76dcd68f3dcb9dc2a7eab9
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254352"
---
# <a name="update-ribbon-customizations-in-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Обновление настроек ленты в проектах Office, переносимых на .NET Framework 4 или .NET Framework 4,5
  Если проект содержит настройку ленты, созданную с помощью элемента проекта **Лента (визуальный конструктор)** , необходимо внести следующие изменения в код проекта, если Целевая платформа изменена на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии.

- Измените созданный код ленты.

- Измените любой код, который создает экземпляры элементов управления ленты во время выполнения, обрабатывает события ленты или программно задает расположение компонента ленты.

## <a name="update-the-generated-ribbon-code"></a>Обновление созданного кода ленты
 Если требуемая версия .NET Framework для проекта изменяется на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию, необходимо изменить созданный код для элемента ленты, выполнив следующие действия. Файлы кода, которые следует обновить, зависят от языка программирования и способа создания проекта.

- В Visual Basic проекты или в визуальных C# проектах, созданных в либо [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] , либо выполните все действия в файле кода программной части ленты (*йоурриббонитем*. Designer.cs или *йоурриббонитем*. Designer. vb). Чтобы просмотреть файл кода программной части в Visual Basic проектах, нажмите кнопку **Показать все файлы** в **Обозреватель решений**.

- В визуальных C# проектах, созданных в Visual Studio 2008 и затем обновленных [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]до, выполните первые два шага в файле кода ленты (*йоурриббонитем*. cs или *йоурриббонитем*. vb) и выполните оставшиеся действия в разделе Файл кода программной части ленты.

### <a name="to-change-the-generated-ribbon-code"></a>Изменение созданного кода ленты

1. Измените объявление класса ленты так, чтобы он был производным от <xref:Microsoft.Office.Tools.Ribbon.RibbonBase>, а не от `Microsoft.Office.Tools.Ribbon.OfficeRibbon`.

2. Измените конструктор класса ленты, как показано ниже. Если в конструктор был добавлен собственный код, не изменяйте его. В проектах Visual Basic измените только конструктор без параметров. Игнорируйте другой конструктор.

     В следующем примере кода показан конструктор по умолчанию для класса ленты в проекте, ориентированном на .NET Framework 3.5.

    ```vb
    Public Sub New()
        MyBase.New()
        InitializeComponent()
    End Sub
    ```

    ```csharp
    public Ribbon1()
    {
        InitializeComponent();
    }
    ```

     В следующем примере кода показан конструктор по умолчанию для класса ленты в проекте, ориентированном на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию.

    ```vb
    Public Sub New()
        MyBase.New(Globals.Factory.GetRibbonFactory())
        InitializeComponent()
    End Sub
    ```

    ```csharp
    public Ribbon1()
        : base(Globals.Factory.GetRibbonFactory())
    {
        InitializeComponent();
    }
    ```

3. В методе `InitializeComponent` измените код, который создает элемент управления ленты, чтобы код использовал один из вспомогательных методов объекта <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>.

    > [!NOTE]
    > В проектах Visual C# необходимо расширить область `Component Designer generated code` так, чтобы она включала метод `InitializeComponent`.

     Например, предположим, что файл содержит следующую строку кода, которая создает экземпляр <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> с именем `button1` в проекте, ориентированном на .NET Framework 3.5.

    ```vb
    Me.button1 = New Microsoft.Office.Tools.Ribbon.RibbonButton()
    ```

    ```csharp
    this.button1 = new Microsoft.Office.Tools.Ribbon.RibbonButton();
    ```

     В проекте, ориентированном на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию, вместо этого необходимо использовать следующий код.

    ```vb
    Me.button1 = Me.Factory.CreateRibbonButton()
    ```

    ```csharp
    this.button1 = this.Factory.CreateRibbonButton();
    ```

     Полный список вспомогательных методов для элементов управления ленты см. в разделе [Создание экземпляров элементов управления ленты](#ribboncontrols).

4. В проектах Visual C# измените любую строку кода в методе `InitializeComponent`, использующем делегат <xref:System.EventHandler%601>, так, чтобы применялся определенный делегат ленты.

     Например, предположим, что файл содержит следующую строку кода, которая обрабатывает событие <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> в проекте, ориентированном на .NET Framework 3.5.

    \<Кодеконтентплацехолдер > 8</CodeContentPlaceHolder> в проекте, ориентированном на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, вместо этого необходимо использовать следующий код.

    \<Кодеконтентплацехолдер > 9</CodeContentPlaceHolder> полный список делегатов ленты см. в разделе [Handle Ribbon Events](#ribbonevents).

5. В проектах Visual Basic найдите класс `ThisRibbonCollection` в конце файла. Измените объявление этого класса так, чтобы он больше не наследовал от `Microsoft.Office.Tools.Ribbon.RibbonReadOnlyCollection`.

## <a name="ribboncontrols"></a>Создание экземпляров элементов управления ленты
 Вам необходимо изменить любой код, который динамически создает элементы управления ленты. В проектах, ориентированных на .NET Framework 3.5, элементы управления ленты — это классы, экземпляры которых можно создавать напрямую в определенных сценариях. В проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, эти элементы управления представляют интерфейсы, которые не могут создаваться напрямую. Необходимо создать элементы управления с помощью методов, предоставляемых объектом <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>.

 Существует два способа доступа к объекту <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>:

- С помощью свойства Factory класса Ribbon. Используйте этот подход в коде в классе ленты.

- С помощью метода `Globals.Factory.GetRibbonFactory`. Используйте этот подход в коде вне класса ленты. Дополнительные сведения о классе Globals см. в разделе [глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md).

  В следующем примере кода показано, как создать <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> в классе ленты в проекте, ориентированном на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию.

\<Кодеконтентплацехолдер > 10</CodeContentPlaceHolder> \<кодеконтентплацехолдер > 11</CodeContentPlaceHolder> в следующей таблице перечислены элементы управления, которые можно создать программно, и метод, используемый для создания элементов управления в проектах, предназначенных для[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии.

|Элемент управления|Метод RibbonFactory, используемый в проектах для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] и более поздних версий|
|-------------| - |
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButton%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButtonGroup%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonCheckBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonComboBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDialogLauncher%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>.|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDown%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDownItem>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDownItem%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonEditBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGallery%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGroup%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonLabel%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonManager>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonManager%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonMenu%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSeparator%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSplitButton%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonTab%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonToggleButton%2A>|

## <a name="ribbonevents"></a>Обработчики событий ленты
 Необходимо изменить любой код, который обрабатывает события элементов управления ленты. В проектах, ориентированных на .NET Framework 3.5, эти события обрабатываются универсальным делегатом <xref:System.EventHandler%601>. В проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, эти события обрабатываются другими делегатами.

 В следующей таблице перечислены события ленты и делегаты, связанные с ними в проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии.

|событие|Делегат, используемый в проектах для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] и более поздних версий|
|-----------| - |
|Событие <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage> в созданном классе ленты|<xref:Microsoft.Office.Tools.Ribbon.RibbonLoadImageEventHandler>|
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>|<xref:Microsoft.Office.Tools.Ribbon.RibbonUIEventHandler>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.SelectionChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventHandler>|

## <a name="set-the-position-of-a-ribbon-component-programmatically"></a>Программное задание расположения компонента ленты
 Необходимо изменить любой код, который задает положение групп, вкладок и элементов управления ленты. В проектах, ориентированных на .NET Framework 3.5, можно использовать статические методы `AfterOfficeId` и `BeforeOfficeId` класса `Microsoft.Office.Tools.Ribbon.RibbonPosition` для установки свойства `Position` группы, вкладки или элемента управления. В проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, необходимо получить доступ к этим методам с помощью свойства <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.RibbonPosition%2A>, предоставляемого объектом <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>.

 Существует два способа доступа к объекту <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>:

- С помощью свойства `Factory` класса ленты. Используйте этот подход в коде в классе ленты.

- С помощью метода `Globals.Factory.GetRibbonFactory`. Используйте этот подход в коде вне класса ленты. Дополнительные сведения о классе Globals см. в разделе [глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md).

  В следующем примере кода показано, как установить свойство `Position` вкладки в классе ленты в проекте, ориентированном на .NET Framework 3.5.

```vb
Me.tab1.Position = RibbonPosition.AfterOfficeId("TabHome")
```

```csharp
this.tab1.Position = RibbonPosition.AfterOfficeId("TabHome");
```

 В следующем примере кода показана та же задача в проекте, ориентированном на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].

```vb
Me.tab1.Position = Me.Factory.RibbonPosition.AfterOfficeId("TabHome")
```

```csharp
this.tab1.Position = this.Factory.RibbonPosition.AfterOfficeId("TabHome");
```

## <a name="see-also"></a>См. также
- [Перенос решений Office на .NET Framework 4 или более поздней версии](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Конструктор лент](../vsto/ribbon-designer.md)
