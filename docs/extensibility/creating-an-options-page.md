---
title: "Создание страницы параметров | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "страницы "Параметры средств" [Visual Studio SDK], создание"
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
caps.latest.revision: 62
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 62
---
# Создание страницы параметров
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В этом пошаговом руководстве создается простой Сервис\/Параметры страницы, использующей сетку свойств для проверки свойств.  
  
 Эти свойства, чтобы сохранить и восстановить их из файла параметров, выполните следующие действия, а затем смотреть [Создание категория параметров](../extensibility/creating-a-settings-category.md).  
  
 MPF предоставляет два класса для создания страницы параметров средств <xref:Microsoft.VisualStudio.Shell.Package> класса и <xref:Microsoft.VisualStudio.Shell.DialogPage> класса. Создайте VSPackage для обеспечения контейнер эти страницы путем создания подклассов класс пакета. Каждая страница параметров инструментов создать путем наследования от класса DialogPage.  
  
## Обязательные компоненты  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Для получения дополнительной информации см. [Установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Создание сетки страницы параметров инструментов  
 В этом разделе создайте простой Сервис Параметры сетки свойств. Используйте эту сетку для отображения и изменения значения свойства.  
  
#### Создание проекта VSIX и добавление VSPackage  
  
1.  Все расширения Visual Studio запускает в проекте развертывания VSIX, который будет содержать средств расширения. Создание [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проект VSIX с именем `MyToolsOptionsExtension`. Можно найти шаблон проекта VSIX в **Новый проект** диалоговом окне под **Visual C\# и расширяемость**.  
  
2.  Добавьте VSPackage, добавив пакет Visual Studio шаблон элемента с именем `MyToolsOptionsPackage`. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **Добавить или создать элемент**. В **диалоговое окно Добавление нового элемента**, последовательно выберите пункты **элементы Visual C\# и расширяемость** и выберите **пакет Visual Studio**. В **имя** в нижней части диалогового окна, измените имя файла `MyToolsOptionsPackage.cs`. Дополнительные сведения о том, как создать пакет VSPackage в разделе [Создание расширения с помощью VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).  
  
#### Чтобы создать Сервис, параметры сетки свойств  
  
1.  Откройте файл MyToolsOptionsPackage в редакторе кода.  
  
2.  Добавьте следующий оператор using.  
  
    ```c#  
    using System.ComponentModel;  
    ```  
  
3.  Объявите класс OptionPageGrid и сделайте его производным от <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
    ```c#  
    public class OptionPageGrid : DialogPage  
    {  }  
    ```  
  
4.  Применить <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> класс VSPackage, чтобы назначить класс категория параметров и OptionPageGrid имя страницы параметров. Результат должен выглядеть следующим образом:  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
5.  Добавление `OptionInteger` Свойства `OptionPageGrid` класса.  
  
    -   Применить <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> Присвоение свойству категорию сетки свойств.  
  
    -   Применение <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> для присвоения свойству имени.  
  
    -   Применить <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> Присвоение свойству описание.  
  
    ```c#  
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
    >  Реализация по умолчанию <xref:Microsoft.VisualStudio.Shell.DialogPage> поддерживает свойства, имеющие соответствующие преобразователи или которые структур или массивов, которые могут быть развернуты в свойства, которые имеют соответствующие преобразователи. Список преобразователи см <xref:System.ComponentModel> пространства имен.  
  
6.  Выполните сборку решения и запустите отладку.  
  
7.  В экспериментальном экземпляре Visual Studio на **средства** меню **Параметры**.  
  
     В левой области появится **Мои категории**. \(Параметры категории перечислены в алфавитном порядке, оно должно отображаться о посередине вниз по списку.\) Откройте **Мои категории** и нажмите кнопку **мою страницу сетки**. Таблица параметров отображается в правой области. Свойства категории **Параметры**, и имя свойства **Мой вариант целое**. Описание свойства **Мой вариант целое**, отображается в нижней части области. Измените значение 256 исходное значение на другое. Щелкните **ОК**, а затем снова откройте **мою страницу сетки**. Вы увидите, что новое значение сохраняется.  
  
     Страница «параметры» также доступна через панель быстрого запуска Visual Studio. Введите в окне быстрый запуск в правом верхнем углу интегрированной среды разработки **Мои категории** и вы увидите **Мои категории –\> мою страницу сетки** перечислены в раскрывающемся списке.  
  
## Создание пользовательского средства параметры страницы  
 В этом разделе создается на странице Параметры средств с помощью пользовательского интерфейса. Эта страница позволяет отображать и изменять значение свойства.  
  
1.  Откройте файл MyToolsOptionsPackage в редакторе кода.  
  
2.  Добавьте следующий оператор using.  
  
    ```vb  
    using System.Windows.Forms;  
    ```  
  
3.  Добавление `OptionPageCustom` класса непосредственно перед `OptionPageGrid` класса. Унаследовать новый класс от `DialogPage`.  
  
    ```c#  
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
  
4.  Добавьте атрибут GUID. Добавьте свойство OptionString:  
  
    ```c#  
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
  
5.  Применить второй <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> класс VSPackage. Этот атрибут присваивается класс категория параметров и имя страницы параметров.  
  
    ```c#  
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
  
6.  Добавить новую **пользовательский элемент управления** с именем MyUserControl в проект.  
  
7.  Добавить **TextBox** управления к пользовательскому элементу управления.  
  
     В **Свойства** на панели инструментов щелкните **событий** кнопку, а затем дважды щелкните **оставить** событий. В коде MyUserControl.cs появляется новый обработчик событий.  
  
8.  Добавьте открытое `OptionsPage` поле, `Initialize` метод для класса элемента управления и обновления, обработчик событий для задания параметра значение содержимое текстового поля:  
  
    ```c#  
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
  
     `optionsPage` Поле содержит ссылку на родительский `OptionPageCustom` экземпляра.`Initialize` Отображает метод `OptionString` в **TextBox**. Обработчик событий записывает текущее значение **TextBox** для `OptionString` когда фокус ввода находится оставляет **TextBox**.  
  
9. В файле кода пакета добавьте переопределение для `OptionPageCustom.Window` Свойства в класс OptionPageCustom для создания, инициализации и возврата экземпляра `MyUserControl`. Класс должен теперь выглядеть следующим образом:  
  
    ```c#  
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
  
11. В экспериментальном экземпляре выберите **инструменты и параметры**.  
  
12. Найти **Мои категории** и **настраиваемые страницы**.  
  
13. Измените значение **OptionString**. Щелкните **ОК**, а затем снова откройте **мою страницу пользовательского**. Вы увидите, что сохранил новое значение.  
  
## Параметры доступа к  
 В этом разделе получить значение параметра из VSPackage, который содержит связанные страницы Параметры средств. Та же технология может использоваться для получения значения любого общедоступного свойства.  
  
1.  Добавьте в файл кода пакета, открытое свойство с именем **OptionInteger** для **MyToolsOptionsPackage** класса.  
  
    ```  
    public int OptionInteger  
    {  
        get  
        {  
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));  
            return page.OptionInteger;  
        }  
    }  
  
    ```  
  
     Этот код вызывает <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> для создания или получения `OptionPageGrid` экземпляра.`OptionPageGrid` вызовы <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> загрузить ее параметров, которые являются открытые свойства.  
  
2.  Теперь добавьте пользовательскую команду шаблон элемента с именем **MyToolsOptionsCommand** для отображения значения. В **Добавление нового элемента** диалоговое окно, последовательно выберите пункты **Visual C\# и расширяемость** и выберите **настраиваемой команды**. В **имя** в нижней части окна, измените имя файла команд для **MyToolsOptionsCommand.cs**.  
  
3.  В файле MyToolsOptionsCommand замените текст команды `ShowMessageBox` следующим:  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;  
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));  
    }  
  
    ```  
  
4.  Выполните сборку решения и запустите отладку.  
  
5.  В экспериментальном экземпляре на **средства** меню, щелкните **вызова MyToolsOptionsCommand**.  
  
     Окно сообщения отображает текущее значение `OptionInteger`.  
  
## См. также  
 [Параметры и параметры страницы](../extensibility/internals/options-and-options-pages.md)