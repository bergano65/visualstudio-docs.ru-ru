---
title: "Обновление настроек ленты в проектах Office, которые переносятся на платформу .NET Framework 4 или .NET Framework 4.5 | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4d3c2e834b3a618bf033ef7f37ca8bbac7d0efcf
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Обновление настроек ленты в проектах Office, которые переносятся на платформу .NET Framework 4 или .NET Framework 4.5
  Если проект содержит настройку ленты, созданной с помощью **Лента (визуальный конструктор)** элемента проекта, необходимо внести следующие изменения в код проекта при изменении целевой версии .NET framework для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или позже.  
  
-   Измените созданный код ленты.  
  
-   Также необходимо изменить любой код, который создает экземпляры элементов управления ленты во время выполнения, обрабатывает события ленты или программно задает положение компонента ленты.  
  
## <a name="updating-the-generated-ribbon-code"></a>Изменение созданного кода ленты  
 Если требуемая версия .NET Framework для проекта изменяется на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию, необходимо изменить созданный код для элемента ленты, выполнив следующие действия. Файлы кода, которые следует обновить, зависят от языка программирования и способа создания проекта.  
  
-   В проектах Visual Basic или в проектах Visual C#, созданных в [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] или [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] выполнять все действия в файле кода ленты (*YourRibbonItem*. Designer.cs или *YourRibbonItem*. Designer.vb). Для просмотра файла кода в проектах Visual Basic щелкните **Показать все файлы** кнопку в **обозревателе решений**.  
  
-   В проектах Visual C#, созданных в Visual Studio 2008 и затем обновленных до [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], выполните первые два действия в файле кода ленты (*YourRibbonItem*.cs или *YourRibbonItem*.vb), и Выполните оставшиеся действия в файле кода ленты.  
  
#### <a name="to-change-the-generated-ribbon-code"></a>Изменение созданного кода ленты  
  
1.  Измените объявление класса ленты, чтобы он был производным от <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> вместо Microsoft.Office.Tools.Ribbon.OfficeRibbon.  
  
2.  Измените конструктор класса ленты, как показано ниже. Если в конструктор был добавлен собственный код, не изменяйте его. В проектах Visual Basic измените только конструктор без параметров. Игнорируйте другой конструктор.  
  
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
  
3.  В методе `InitializeComponent` измените код, который создает элемент управления ленты, чтобы код использовал один из вспомогательных методов объекта <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>.  
  
    > [!NOTE]  
    >  В проектах Visual C# необходимо расширить область `Component Designer generated code` так, чтобы она включала метод `InitializeComponent`.  
  
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
  
     Полный список вспомогательных методов для элементов управления ленты см. в разделе [создание экземпляров элементов управления ленты](#ribboncontrols).  
  
4.  В проектах Visual C# измените любую строку кода в методе `InitializeComponent`, использующем делегат <xref:System.EventHandler%601>, так, чтобы применялся определенный делегат ленты.  
  
     Например, предположим, что файл содержит следующую строку кода, которая обрабатывает событие <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> в проекте, ориентированном на .NET Framework 3.5.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
     В проекте, ориентированном на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию, вместо этого необходимо использовать следующий код.  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
     Полный список делегатов ленты см. в разделе [обработка событий ленты](#ribbonevents).  
  
5.  В проектах Visual Basic найдите класс `ThisRibbonCollection` в конце файла. Измените объявление этого класса, чтобы он больше не наследует от Microsoft.Office.Tools.Ribbon.RibbonReadOnlyCollection.  
  
##  <a name="ribboncontrols"></a>При создании элементов управления ленты  
 Вам необходимо изменить любой код, который динамически создает элементы управления ленты. В проектах, ориентированных на .NET Framework 3.5, элементы управления ленты — это классы, экземпляры которых можно создавать напрямую в определенных сценариях. В проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, эти элементы управления представляют интерфейсы, которые не могут создаваться напрямую. Необходимо создать элементы управления с помощью методов, предоставляемых объектом <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>.  
  
 Существует два способа доступа к объекту <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>:  
  
-   С помощью свойства фабрики класса ленты. Используйте этот подход в коде в классе ленты.  
  
-   С помощью метода Globals.Factory.GetRibbonFactory. Используйте этот подход в коде вне класса ленты. Дополнительные сведения о классе глобальных переменных см. в разделе [глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 В следующем примере кода показано, как создать <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> в классе ленты в проекте, ориентированном на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию.  
  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>11</CodeContentPlaceHolder>  
 В следующей таблице перечислены элементы управления, которые можно создавать программно, и метод, используемый для создания элементов управления в проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии.  
  
|Элемент управления|Метод RibbonFactory, используемый в проектах для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] и более поздних версий|  
|-------------|---------------------------------------------------------------------------------------------------------------|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButton%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButtonGroup%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonCheckBox%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonComboBox%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDialogLauncher%2A>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>:|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDown%2A>|  
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
  
##  <a name="ribbonevents"></a>Обработка событий ленты  
 Необходимо изменить любой код, который обрабатывает события элементов управления ленты. В проектах, ориентированных на .NET Framework 3.5, эти события обрабатываются универсальным делегатом <xref:System.EventHandler%601>. В проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, эти события обрабатываются другими делегатами.  
  
 В следующей таблице перечислены события ленты и делегаты, связанные с ними в проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии.  
  
|событие|Делегат, используемый в проектах для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] и более поздних версий|  
|-----------|---------------------------------------------------------------------------------------------------|  
|Событие <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage> в созданном классе ленты|<xref:Microsoft.Office.Tools.Ribbon.RibbonLoadImageEventHandler>|  
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>|<xref:Microsoft.Office.Tools.Ribbon.RibbonUIEventHandler>|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.SelectionChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventHandler>|  
  
## <a name="setting-the-position-of-a-ribbon-component-programmatically"></a>Программная установка положения компонента ленты  
 Необходимо изменить любой код, который задает положение групп, вкладок и элементов управления ленты. В проектах, ориентированных на .NET Framework 3.5, вы можно использовать методы AfterOfficeId и BeforeOfficeId статического класса Microsoft.Office.Tools.Ribbon.RibbonPosition Чтобы назначить свойство для группы, вкладки или элемента управления. В проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, необходимо получить доступ к этим методам с помощью свойства <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.RibbonPosition%2A>, предоставляемого объектом <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>.  
  
 Существует два способа доступа к объекту <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>:  
  
-   С помощью свойства фабрики класса ленты. Используйте этот подход в коде в классе ленты.  
  
-   С помощью метода Globals.Factory.GetRibbonFactory. Используйте этот подход в коде вне класса ленты. Дополнительные сведения о классе глобальных переменных см. в разделе [глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 В следующем примере кода показано, как задать свойство положение вкладки в классе ленты в проекте, ориентированном на .NET Framework 3.5.  
  
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
 [Migrating Office Solutions to the .NET Framework 4 or later](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Конструктор лент](../vsto/ribbon-designer.md)  
  
  