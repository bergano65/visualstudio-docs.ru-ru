---
title: "Создание страницы параметров | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
caps.latest.revision: "62"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 68a3afc0a83d4dba7b7cd46b2b1eba23695a2848
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="creating-an-options-page"></a>Создание страницы параметров
В этом пошаговом руководстве создается простой Сервис/Параметры страницы, использующей сетку свойств для проверки и задать свойства.  
  
 Для этих свойств, чтобы сохранить и восстановить их из файла параметров, выполните следующие действия, а затем посмотреть [Создание категории параметров](../extensibility/creating-a-settings-category.md).  
  
 MPF предоставляет два класса для создания страницы параметров средств <xref:Microsoft.VisualStudio.Shell.Package> класса и <xref:Microsoft.VisualStudio.Shell.DialogPage> класса. Создаваемый пакет VSPackage для предоставления контейнер для этих страниц путем создания подклассов класса пакета. Создайте каждой страницы настроек инструментов путем наследования от класса DialogPage.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-tools-options-grid-page"></a>Создание сетки страницы настроек инструментов  
 В этом разделе создайте простую сетку свойств параметров средств. Используйте эту сетку для отображения и изменения значения свойства.  
  
#### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Создание проекта VSIX и добавление пакетов VSPackage  
  
1.  Все расширения Visual Studio начинается с проект развертывания VSIX, который будет содержать средств расширения. Создание [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проект VSIX с именем `MyToolsOptionsExtension`. Шаблон проекта VSIX в можно найти **новый проект** диалогового окна в разделе **Visual C# / Extensibility**.  
  
2.  Добавьте VSPackage, добавив элемент шаблона пакета Visual Studio с именем `MyToolsOptionsPackage`. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **добавить / новый элемент**. В **диалоговое окно добавления нового элемента**, перейдите в меню **элементы Visual C# / Extensibility** и выберите **пакета Visual Studio**. В **имя** в нижней части диалогового окна, измените имя файла для `MyToolsOptionsPackage.cs`. Дополнительные сведения о том, как создать пакет VSPackage см. в разделе [создания расширения с VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).  
  
#### <a name="to-create-the-tools-options-property-grid"></a>Создание сетки свойств Сервис — Параметры  
  
1.  Откройте файл MyToolsOptionsPackage в редакторе кода.  
  
2.  Добавьте следующий код с помощью инструкции.  
  
    ```csharp  
    using System.ComponentModel;  
    ```  
  
3.  Объявить класс OptionPageGrid и сделайте его производным от <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  }  
    ```  
  
4.  Применить <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> класс VSPackage, чтобы присвоить классу параметры категории и имя страницы параметров для OptionPageGrid. Результат должен выглядеть следующим образом:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
5.  Добавить `OptionInteger` свойства `OptionPageGrid` класса.  
  
    -   Применить <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> необходимо присвоить свойству категорию сетки свойств.  
  
    -   Применить <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> для присвоения свойству имени.  
  
    -   Применить <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> необходимо присвоить свойству описание.  
  
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
    >  Реализация по умолчанию <xref:Microsoft.VisualStudio.Shell.DialogPage> поддерживает свойства, имеющие соответствующие преобразователи типов или таблицы, структур или массивов, которые могут быть развернуты в свойства, имеющие соответствующие преобразователи типов. Список преобразователи типов см. в разделе <xref:System.ComponentModel> пространства имен.  
  
6.  Выполните сборку решения и запустите отладку.  
  
7.  В экспериментальном экземпляре Visual Studio на **средства** меню **параметры**.  
  
     В левой области отобразится **Мои категории**. (Параметры категории перечислены в алфавитном порядке, поэтому она должна отображаться о посередине вниз по списку.) Откройте **Мои категории** и нажмите кнопку **мою страницу сетки**. В сетку параметров отображается на правой панели. Свойства категории **параметры моей**, и имя свойства **Мои целочисленный параметр**. Описание свойства **Мой целочисленный параметр**, отображается в нижней части области. Измените значение 256 исходное значение на другое. Нажмите кнопку **ОК**, а затем снова открыть **мою страницу сетки**. Вы увидите, что новое значение сохраняется.  
  
     Страница «параметры» также доступна через быстрого запуска Visual Studio. В правом верхнем углу интегрированной среды разработки окна быстрого запуска, введите **Мои категории** и вы увидите **Мои категории -> Мой страницы сетки** перечислены в раскрывающемся списке.  
  
## <a name="creating-a-tools-options-custom-page"></a>Создание пользовательского средства параметры страницы  
 В этом разделе создается на странице Параметры средств с настраиваемого пользовательского интерфейса. Эта страница позволяет отображать и изменять значение свойства.  
  
1.  Откройте файл MyToolsOptionsPackage в редакторе кода.  
  
2.  Добавьте следующий код с помощью инструкции.  
  
    ```vb  
    using System.Windows.Forms;  
    ```  
  
3.  Добавить `OptionPageCustom` класса непосредственно перед `OptionPageGrid` класса. Наследовать новый класс из `DialogPage`.  
  
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
  
4.  Добавьте атрибут GUID. Добавьте свойство OptionString:  
  
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
  
5.  Применить второй <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> класс VSPackage. Этот атрибут назначает класс параметры категории и имя страницы параметров.  
  
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
  
6.  Добавьте новый **пользовательский элемент управления** с именем MyUserControl в проект.  
  
7.  Добавить **TextBox** элемента управления в пользовательский элемент управления.  
  
     В **свойства** на панели инструментов щелкните **событий** кнопку, а затем дважды щелкните **оставить** событий. В коде MyUserControl.cs появляется новый обработчик событий.  
  
8.  Добавить открытый `OptionsPage` поля, `Initialize` метод для класса элемента управления и обновления, обработчик событий для задания параметра значение к содержимому текстового поля:  
  
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
  
     `optionsPage` Поле содержит ссылку на родительский объект `OptionPageCustom` экземпляра. `Initialize` Метод выводит `OptionString` в **TextBox**. Обработчик событий записывает текущее значение **TextBox** для `OptionString` когда фокус ввода находится оставляет **TextBox**.  
  
9. В файле кода пакета добавьте переопределение для `OptionPageCustom.Window` свойство классу OptionPageCustom для создания, инициализации и возвратить экземпляр `MyUserControl`. Класс должен выглядеть следующим образом:  
  
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
  
11. В экспериментальном экземпляре выберите **Сервис / Параметры**.  
  
12. Найти **Мои категории** и затем **настраиваемые страницы**.  
  
13. Измените значение **OptionString**. Нажмите кнопку **ОК**, а затем снова открыть **Мои настраиваемой страницы**. Вы увидите, что новое значение имеет постоянное.  
  
## <a name="accessing-options"></a>Параметры доступа к  
 В этом разделе получить значение параметра из пакета VSPackage, на котором размещена связанной страницы параметров средств. Тот же метод можно использовать для получения значения любого общедоступного свойства.  
  
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
  
     Этот код вызывает <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> для создания или получения `OptionPageGrid` экземпляра. `OptionPageGrid`вызовы <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> загрузить ее параметров, которые являются открытые свойства.  
  
2.  Теперь добавьте пользовательскую команду шаблон элемента с именем **MyToolsOptionsCommand** для отображения значения. В **Добавление нового элемента** диалоговое окно, перейдите на **Visual C# / Extensibility** и выберите **настраиваемой команды**. В **имя** в нижней части окна, измените имя файла команд для **MyToolsOptionsCommand.cs**.  
  
3.  Замените текст команды в файле MyToolsOptionsCommand `ShowMessageBox` метод со следующими:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;  
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));  
    }  
  
    ```  
  
4.  Выполните сборку решения и запустите отладку.  
  
5.  В экспериментальном экземпляре на **средства** меню, нажмите кнопку **MyToolsOptionsCommand вызова**.  
  
     Окно сообщения отображает текущее значение `OptionInteger`.  
  
## <a name="see-also"></a>См. также  
 [Параметры и страницы параметров](../extensibility/internals/options-and-options-pages.md)