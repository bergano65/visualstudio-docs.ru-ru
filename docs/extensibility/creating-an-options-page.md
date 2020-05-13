---
title: Создание страницы опционов (ru) Документы Майкрософт
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1607af2a6f68bd5593f9a185188b25b364926fe4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739516"
---
# <a name="create-an-options-page"></a>Создание страницы опций

Это пошаговое решение создает простую страницу «Инструменты/Параметры», которая использует сетку свойств для изучения и установки свойств.

 Чтобы сохранить эти свойства, чтобы восстановить их из файла настроек, выполните следующие действия, а затем [см. Создать категорию параметров.](../extensibility/creating-a-settings-category.md)

 MPF предоставляет два класса, которые помогут <xref:Microsoft.VisualStudio.Shell.Package> вам создать <xref:Microsoft.VisualStudio.Shell.DialogPage> страницы параметры инструментов, класс и класс. Вы создаете VSPackage, чтобы обеспечить контейнер для `Package` этих страниц, подклассифицируя класс. Вы создаете каждую страницу параметров инструментов, выражаясь из `DialogPage` класса.

## <a name="prerequisites"></a>Предварительные требования

 Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-tools-options-grid-page"></a>Создание страницы сетки опций инструментов

 В этом разделе создается простая сетка свойств опций инструментов. Эта сетка используется для отображения и изменения значения свойства.

### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Создать проект VSIX и добавить VSPackage

1. Каждое расширение Visual Studio начинается с проекта развертывания VSIX, который будет содержать активы расширения. Создайте [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проект VSIX под названием `MyToolsOptionsExtension`. Шаблон проекта VSIX можно найти в диалоге **нового проекта,** ища "vsix".

2. Добавить VSPackage, добавив шаблон элемента `MyToolsOptionsPackage`Visual Studio Package под названием. В **Solution Explorer**, правой кнопкой мыши узла проекта и выберите **Добавить** > **новый пункт**. В **диалоге Добавить новый элемент**, перейдите на **Visual C' Элементы** > **Расширяемость** и выберите **Visual Studio Пакет**. В поле **«Имя»** в нижней части диалога `MyToolsOptionsPackage.cs`измените имя файла на . Для получения дополнительной информации о том, как создать VSPackage, [см. Создать расширение с VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).

### <a name="to-create-the-tools-options-property-grid"></a>Создание сетки свойств «Инструменты параметры»

1. Откройте файл *MyToolsOptionsPackage* в редакторе кода.

2. Добавьте следующее заявление с помощью.

   ```csharp
   using System.ComponentModel;
   ```

3. Объявить `OptionPageGrid` класс и <xref:Microsoft.VisualStudio.Shell.DialogPage>получить его из .

   ```csharp
   public class OptionPageGrid : DialogPage
   {  }
   ```

4. Примените <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> `VSPackage` к классу, чтобы назначить классу категорию опций и название страницы optionPage для OptionPageGrid. Результат должен выглядеть следующим образом:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

5. Добавьте `OptionInteger` свойство `OptionPageGrid` в класс.

    - Примените <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> для присвоения свойству категорию сетки свойств.

    - Примените для <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> присвоения в собственность имени.

    - Примените для <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> присвоения в собственность описания.

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;

        [Category("My Category")]
        [DisplayName("My Integer Option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
    }
    ```

    > [!NOTE]
    > Реализация по <xref:Microsoft.VisualStudio.Shell.DialogPage> умолчанию поддерживает свойства, которые имеют соответствующие преобразователи или которые являются структурами или массивами, которые могут быть расширены в свойства, которые имеют соответствующие преобразователи. Список преобразователей <xref:System.ComponentModel> можно узнать из пространства имен.

6. Выполните сборку решения и запустите отладку.

7. В экспериментальном экземпляре Visual Studio, в меню **Tools** нажмите **Параметры**.

     В левом стеле, вы должны увидеть **моя категория**. (Категории опционов перечислены в алфавитном порядке, поэтому они должны отображаться примерно на полпути вниз по списку.) Откройте **мою категорию,** а затем нажмите **Моя страница сетки**. Сетка опций отображается в правом стене. Категория собственности **Мои варианты**, и имя собственности **Мой вариант Integer**. Описание свойства, **Мой вариант integer**, появляется в нижней части панели. Измените значение с его первоначального значения 256 на что-то другое. Нажмите **OK**, а затем вновь открыть **мою страницу сетки**. Вы можете видеть, что новое значение сохраняется.

     Страница опций также доступна через поле поиска Visual Studio. В поле поиска в верхней части IDE введите **мою категорию,** и вы увидите **мою категорию -> страница моей сетки,** указанная в результатах.

## <a name="create-a-tools-options-custom-page"></a>Создание пользовательской страницы «Параметры инструментов»

 В этом разделе создается страница Параметры инструментов с пользовательским пользовательским пользовательским использованием. Вы используете эту страницу для отображения и изменения значения свойства.

1. Откройте файл *MyToolsOptionsPackage* в редакторе кода.

2. Добавьте следующее заявление с помощью.

    ```csharp
    using System.Windows.Forms;
    ```

3. Добавьте `OptionPageCustom` класс непосредственно `OptionPageGrid` перед классом. Вывести новый `DialogPage`класс из .

    ```csharp
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }
    }
    ```

4. Добавьте атрибут GUID. Добавьте свойство OptionString:

    ```csharp
    [Guid("00000000-0000-0000-0000-000000000000")]
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }
    }
    ```

5. Примените <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> секунду к классу VSPackage. Этот атрибут присваивает классу категорию опций и имя страницы.

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    [ProvideOptionPage(typeof(OptionPageCustom),
        "My Category", "My Custom Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

6. Добавьте в проект новый **пользовательский контроль** под названием MyUserControl.

7. Добавьте элемент управления **TextBox** в управление пользователя.

     В окне **Свойств,** на панели инструментов, нажмите кнопку **События,** а затем дважды щелкните событие **«Оставить».** Новый обработчик событий отображается в *коде MyUserControl.cs.*

8. Добавьте `OptionsPage` общедоступное `Initialize` поле, метод в класс управления и обновите обработчик событий, чтобы установить значение опции для содержимого текстового поля:

    ```csharp
    public partial class MyUserControl : UserControl
    {
        public MyUserControl()
        {
            InitializeComponent();
        }

        internal OptionPageCustom optionsPage;

        public void Initialize()
        {
            textBox1.Text = optionsPage.OptionString;
        }

        private void textBox1_Leave(object sender, EventArgs e)
        {
            optionsPage.OptionString = textBox1.Text;
        }
    }
    ```

     Поле `optionsPage` содержит ссылку на `OptionPageCustom` родительский экземпляр. Метод `Initialize` `OptionString` отображается в **TextBox**. Обработчик событий записывает текущее значение `OptionString` **TextBox** к тому, когда фокус покидает **TextBox.**

9. В файле кода пакета добавьте `OptionPageCustom.Window` переопределение `OptionPageCustom` для свойства в класс, чтобы создать, инициализировать и вернуть экземпляр `MyUserControl`. Класс теперь должен выглядеть следующим образом:

    ```csharp
    [Guid("00000000-0000-0000-0000-000000000000")]
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }

        protected override IWin32Window Window
        {
            get
            {
                MyUserControl page = new MyUserControl();
                page.optionsPage = this;
                page.Initialize();
                return page;
            }
        }
    }
    ```

10. Постройте и запустите проект.

11. В экспериментальном примере нажмите > **«Инструменты параметры».** **Tools**

12. Найти **мою категорию,** а затем **моя пользовательская страница**.

13. Измените значение **OptionString**. Нажмите **OK**, а затем вновь открыть **мою пользовательскую страницу**. Вы можете видеть, что новое значение сохраняется.

## <a name="access-options"></a>Параметры доступа

 В этом разделе вы получаете значение опции от VSPackage, в котором размещена страница связанных опций инструментов. Тот же метод может быть использован для получения стоимости любой государственной собственности.

1. В файле кода пакета добавьте общедоступное свойство **OptionInteger** в класс **MyToolsOptionsPackage.**

    ```csharp
    public int OptionInteger
    {
        get
        {
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));
            return page.OptionInteger;
        }
    }

    ```

     Этот код <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> требует создания или `OptionPageGrid` извлечения экземпляра. `OptionPageGrid`вызовы <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> для загрузки его опций, которые являются общественными свойствами.

2. Теперь добавьте пользовательский шаблон элемента команды под названием **MyToolsOptionsCommand** для отображения значения. В диалоге **Добавить новый элемент** перейдите на **Visual C е** > **Extensibility** и выберите **пользовательские команды.** В поле **«Имя»** в нижней части окна измените имя файла команды на *MyToolsOptionsCommand.cs.*

3. В файле *MyToolsOptionsCommand* замените тело метода `ShowMessageBox` команды следующим:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));
    }

    ```

4. Выполните сборку решения и запустите отладку.

5. В экспериментальном примере, в меню **Tools,** нажмите **Наймите Вызвать MyToolsOptionsCommand**.

     Коробка сообщений отображает текущее `OptionInteger`значение.

## <a name="see-also"></a>См. также

- [Страницы вариантов и опций](../extensibility/internals/options-and-options-pages.md)
