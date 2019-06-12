---
title: Обновление областей формы Outlook в проектах миграции на .NET Framework 4, 4.5
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
ms.openlocfilehash: e7e300cd9f6f7d631a029310b01fbfdad7cb4686
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2019
ms.locfileid: "66836047"
---
# <a name="update-form-regions-in-outlook-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Обновление областей формы в проектах Outlook, которые переносятся на .NET Framework 4 или .NET Framework 4.5
  Если требуемая версия .NET Framework для проекта надстройки VSTO для Outlook с областью формы изменяется на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию, необходимо внести некоторые изменения в создаваемый код области формы и в любой код, который создает экземпляры определенных классов области формы во время выполнения.

## <a name="update-the-generated-form-region-code"></a>Обновить созданный код области формы
 Если требуемая версия .NET Framework проекта изменяется на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию, необходимо изменить созданный код области формы. Вносимые изменения отличаются для областей форм, которые были разработаны в Visual Studio, и для областей форм, импортированных из Outlook. Дополнительные сведения об отличиях этих типов областей форм см. в разделе [областей форм Outlook создайте](../vsto/creating-outlook-form-regions.md).

### <a name="to-update-the-generated-code-for-a-form-region-that-you-designed-in-visual-studio"></a>Обновление созданного кода для области формы, разработанной в Visual Studio

1. Откройте файл кода программной части области формы в редакторе кода. Этот файл называется *Область_формы*.Designer.cs или *Область_формы*.Designer.vb. Для просмотра файла в проектах Visual Basic нажмите кнопку **Показать все файлы** в **обозревателе решений**.

2. Измените объявление класса области формы так, чтобы он был производным от <xref:Microsoft.Office.Tools.Outlook.FormRegionBase>, а не от `Microsoft.Office.Tools.Outlook.FormRegionControl`.

3. Измените конструктор класса области формы, как показано в следующем примере кода.

     В следующем примере кода показан конструктор для класса области формы в проекте, ориентированном на .NET Framework 3.5.

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(formRegion)
        Me.InitializeComponent()
    End Sub
    ```

    ```csharp
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(formRegion)
    {
        this.InitializeComponent();
    }
    ```

     В следующем примере кода показан конструктор для класса области формы в проекте, ориентированном на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(Globals.Factory, formRegion)
        Me.InitializeComponent()
    End Sub
    ```

    ```csharp
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(Globals.Factory, formRegion)
    {
        this.InitializeComponent();
    }
    ```

4. Измените сигнатуру метода `InitializeManifest` , как показано ниже. Не изменяйте код этого метода. Этот код представляет параметры области формы, которые были применены в конструкторе. В проектах Visual C# необходимо расширить область `Form Region Designer generated code` так, чтобы она включала этот метод.

     В следующем примере кода показана сигнатура метода `InitializeManifest` в проекте, ориентированном на .NET Framework 3.5.

    ```vb
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest)

        ' Do not change code in this method.
    End Sub
    ```

    ```csharp
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest)
    {
        // Do not change code in this method.
    }
    ```

     В следующем примере кода показана сигнатура метода `InitializeManifest` в проекте, ориентированном на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].

    ```vb
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest,
        ByVal factory As Microsoft.Office.Tools.Outlook.Factory)

        ' Do not change code in this method.
    End Sub
    ```

    ```csharp
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest,
        Microsoft.Office.Tools.Outlook.Factory factory)
    {
        // Do not change code in this method.
    }
    ```

5. Добавьте новый элемент области формы Outlook в проект. Откройте файл кода программной части для новой области формы, найдите классы *YourNewFormRegion*`Factory` и `WindowFormRegionCollection` , а затем скопируйте их в буфер обмена.

6. Удалите новую область формы, добавленную в проект.

7. В файле кода программной части области формы, которая обновляется для работы в новом проекте, найдите классы *YourOriginalFormRegion*`Factory` и `WindowFormRegionCollection` и замените код, который был скопирован из новой области формы.

8. В классах *YourNewFormRegion*`Factory` и `WindowFormRegionCollection` найдите все ссылки на класс *YourNewFormRegion* и измените их так, чтобы они указывали на класс *YourOriginalFormRegion* . Например, если имя обновляемой области формы — `SalesDataFormRegion` , а имя новой области формы, созданной на шаге 5, — `FormRegion1`, измените все ссылки для `FormRegion1` на `SalesDataFormRegion`.

#### <a name="to-update-the-generated-code-for-a-form-region-that-you-imported-from-outlook"></a>Обновление созданного кода для области формы, импортированной из Outlook

1. Откройте файл кода программной части области формы в редакторе кода. Этот файл называется *Область_формы*.Designer.cs или *Область_формы*.Designer.vb. Для просмотра файла в проектах Visual Basic нажмите кнопку **Показать все файлы** в **обозревателе решений**.

2. Измените объявление класса области формы так, чтобы он был производным от <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase>, а не от `Microsoft.Office.Tools.Outlook.ImportedFormRegion`.

3. Измените конструктор класса области формы, как показано в следующем примере кода.

     В следующем примере кода показан конструктор для класса области формы в проекте, ориентированном на .NET Framework 3.5.

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(formRegion)
    End Sub
    ```

    ```csharp
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(formRegion)
    {
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);
    }
    ```

     В следующем примере кода показана сигнатура конструктора класса области формы в проекте, ориентированном на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(Globals.Factory, formRegion)
    End Sub
    ```

    ```csharp
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(Globals.Factory, formRegion)
    {
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);
    }
    ```

4. Для каждой строки кода в методе `InitializeControls` , который инициализирует элемент управления в классе области формы, измените код, как показано ниже.

     В следующем примере кода показано, как инициализировать элемент управления в проекте, ориентированном на .NET Framework 3.5. В этом коде метод `GetFormRegionControl` содержит параметр типа, который определяет тип возвращаемого элемента управления.

    ```vb
    Me.olkTextBox1 = Me.GetFormRegionControl(Of Microsoft.Office.Interop.Outlook.OlkTextBox)("OlkTextBox1")
    ```

    ```csharp
    this.olkTextBox1 = this.GetFormRegionControl<Microsoft.Office.Interop.Outlook.OlkTextBox>("OlkTextBox1");
    ```

     В следующем примере кода показано, как инициализировать элемент управления в проекте, ориентированном на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. В этом коде у метода <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase.GetFormRegionControl%2A> нет параметра типа. Необходимо привести возвращаемое значение к типу инициализируемого элемента управления.

    ```vb
    Me.olkTextBox1 = CType(GetFormRegionControl("OlkTextBox1"), Microsoft.Office.Interop.Outlook.OlkTextBox)
    ```

    ```csharp
    this.olkTextBox1 = (Microsoft.Office.Interop.Outlook.OlkTextBox)GetFormRegionControl("OlkTextBox1");
    ```

5. Добавьте новый элемент области формы Outlook в проект. Откройте файл кода программной части для новой области формы, найдите классы *YourNewFormRegion*`Factory` и `WindowFormRegionCollection` , а затем скопируйте их в буфер обмена.

6. Удалите новую область формы, добавленную в проект.

7. В файле кода программной части области формы, которая обновляется для работы в новом проекте, найдите классы *YourOriginalFormRegion*`Factory` и `WindowFormRegionCollection` и замените код, который был скопирован из новой области формы.

8. В классах *YourNewFormRegion*`Factory` и `WindowFormRegionCollection` найдите все ссылки на класс *YourNewFormRegion* и измените их так, чтобы они указывали на класс *YourOriginalFormRegion* . Например, если имя обновляемой области формы — `SalesDataFormRegion` , а имя новой области формы, созданной на шаге 5, — `FormRegion1`, измените все ссылки для `FormRegion1` на `SalesDataFormRegion`.

## <a name="instantiate-form-region-classes"></a>Создавать экземпляры классов области формы
 Вам необходимо изменить любой код, который динамически создает экземпляры классов области формы. В проектах, предназначенных для .NET Framework 3.5, можно создавать экземпляры классов области формы, такие как `Microsoft.Office.Tools.Outlook.FormRegionManifest`, напрямую. В проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии, эти классы представляют интерфейсы, которые не могут создаваться напрямую.

 Если требуемая версия .NET Framework для проекта изменяется на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более позднюю версию, необходимо создать экземпляр интерфейсов с помощью методов, предоставляемых свойством `Globals.Factory`. Дополнительные сведения о `Globals.Factory` свойство, см. в разделе [глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md).

 В следующей таблице перечислены типы областей формы и методы, используемые для создания экземпляров типов в проектах, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или более поздней версии.

|Тип|Фабричный метод, который необходимо использовать|
|----------|---------------------------|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionCustomAction>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionCustomAction%2A>|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionInitializingEventArgs%2A>|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionManifest%2A>|

## <a name="see-also"></a>См. также
- [Перенос решений Office на .NET Framework 4 или более поздней версии](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Создание областей форм Outlook](../vsto/creating-outlook-form-regions.md)
