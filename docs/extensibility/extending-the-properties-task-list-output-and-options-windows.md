---
title: Расширение свойств, список задач, выходные данные и параметры Windows | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4be06a69eac693e951407ecf4c04eabff7bbb31c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54933247"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>Расширение windows свойства, список задач, выходные данные и параметры
Можно получить доступ к любого окна инструментов в Visual Studio. В этом пошаговом руководстве показано, как интегрировать сведения о вашего окна инструментов в новую **параметры** страницы и новый параметр на **свойства** страницы, а также способ записи **список задач** и **вывода** windows.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установить пакет SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-an-extension-with-a-tool-window"></a>Создание расширения с окном инструментов  
  
1.  Создайте проект с именем **TodoList** с помощью шаблона VSIX и добавление шаблона элемента окна пользовательского инструмента с именем **TodoWindow**.  
  
    > [!NOTE]
    >  Дополнительные сведения о создании расширения с окном инструментов, см. в разделе [создание расширения с окном инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="set-up-the-tool-window"></a>Настройка окна инструментов  
 Добавление текстового поля для ввода нового элемента ToDo, кнопку, чтобы добавить новый элемент в список и элемент ListBox для отображения элементов в списке.  
  
1.  В *TodoWindow.xaml*, удалить элементы управления Button, TextBox и StackPanel от UserControl.  
  
    > [!NOTE]
    >  При этом не удаляются **button1_Click** обработчик событий, который будет использовать в дальнейшем.  
  
2.  Из **все элементы управления WPF** раздел **элементов**, перетащите **холст** элемента управления в сетку.  
  
3.  Перетащите **TextBox**, **кнопку**и **ListBox** на холст. Упорядочивание элементов, чтобы текстовое поле и кнопку на одном уровне, и ListBox заполняет остальную часть окна под ними, как показано на рисунке ниже.  
  
     ![Окно инструментов завершения](../extensibility/media/t5-toolwindow.png "T5-окно инструментов")  
  
4.  В области XAML найти кнопку и установите его свойство содержимого **добавить**. Повторное подключение в обработчик событий кнопки в элемент управления Button, добавив `Click="button1_Click"` атрибута. Холст Блок должен выглядеть следующим образом:  
  
    ```xml  
    <Canvas HorizontalAlignment="Left" Width="306">  
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>  
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>  
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>  
    </Canvas>  
    ```  
  
### <a name="customize-the-constructor"></a>Настройка конструктора  
  
1.  В *TodoWindowControl.xaml.cs* файл, добавьте следующий оператор using:  
  
    ```csharp  
    using System;  
    ```  
  
2.  Добавьте открытый ссылку TodoWindow и принимать параметр TodoWindow конструктор TodoWindowControl. Код должен выглядеть следующим образом:  
  
    ```csharp  
    public TodoWindow parent;  
  
    public TodoWindowControl(TodoWindow window)  
    {  
        InitializeComponent();  
        parent = window;  
    }  
    ```  
  
3.  В *TodoWindow.cs*, измените конструктор TodoWindowControl необходимо добавить параметр TodoWindow. Код должен выглядеть следующим образом:  
  
    ```csharp  
    public TodoWindow() : base(null)  
    {  
        this.Caption = "TodoWindow";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
  
         this.Content = new TodoWindowControl(this);  
    }  
    ```  
  
## <a name="create-an-options-page"></a>Создайте страницу параметров  
 Можно указать страницу в **параметры** диалоговое окно, чтобы пользователи могут изменять параметры для окна инструментов. Создание страницы параметров требует как класс, который описывает параметры и запись в *TodoListPackage.cs* или *TodoListPackage.vb* файла.  
  
1. Добавьте класс с именем `ToolsOptions.cs`. Сделать `ToolsOptions` наследовать класс от <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
   ```csharp  
   class ToolsOptions : DialogPage  
   {  
   }  
   ```  
  
2. Добавьте следующий оператор using:  
  
   ```csharp  
   using Microsoft.VisualStudio.Shell;  
   ```  
  
3. На странице "Параметры" в этом пошаговом руководстве предоставляет только один параметр под названием DaysAhead. Добавьте закрытое поле с именем **daysAhead** и свойство с именем **DaysAhead** для `ToolsOptions` класса:  
  
   ```csharp  
   private double daysAhead;  
  
   public double DaysAhead  
   {  
       get { return daysAhead; }  
       set { daysAhead = value; }  
   }  
   ```  
  
   Теперь необходимо убедиться в проект о странице "Параметры".  
  
### <a name="make-the-options-page-available-to-users"></a>Предоставления пользователям страницы параметров  
  
1.  В *TodoWindowPackage.cs*, добавьте <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> для `TodoWindowPackage` класса:  
  
    ```csharp  
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]  
    ```  
  
2.  Первый параметр в конструктор ProvideOptionPage является типом класса `ToolsOptions`, которая была создана ранее. Второй параметр «ToDo», — это имя категории в **параметры** диалоговое окно. Третий параметр, «Общие», — это имя подкатегории **параметры** диалоговое окно, где будут доступны страницы параметров. Следующие два параметра являются идентификаторы ресурсов для строки; Первый — имя категории, а второй — имя подкатегории. Последний параметр определяет, возможен ли эта страница с помощью автоматизации.  
  
     Когда пользователь открывает страницу параметров, она должна иметь вид следующем рисунке.  
  
     ![Страница параметров](../extensibility/media/t5optionspage.gif "T5OptionsPage")  
  
     Обратите внимание, что категория **ToDo** и подкатегорию **Общие**.  
  
## <a name="make-data-available-to-the-properties-window"></a>Сделать данные доступными в окне «Свойства»  
 Вы можете предоставить сведения о списке ToDo, создав класс с именем `TodoItem` , хранит сведения об отдельных элементов в списке ToDo.  
  
1.  Добавьте класс с именем `TodoItem.cs`.  
  
     Когда окно инструментов станет доступным для пользователей, получает элементы в поле со списком TodoItems. Когда пользователь выбирает один из этих элементов в поле со списком **свойства** окне будут отображаться сведения об элементе.  
  
     Чтобы сделать данные доступными в **свойства** окне вам превратить данные в открытых свойств, которые имеют две специальные атрибуты, `Description` и `Category`. `Description` — Это текст, отображаемый в нижней части **свойства** окна. `Category` Определяет, где свойство должно выглядеть при **свойства** окно отображается в **по категориям** представления. На следующем рисунке **свойства** окно находится в **по категориям** представление, **имя** свойство в **поля ToDo** категории флажок установлен и описание **имя** свойство отображается в нижней части окна.  
  
     ![Окно "Свойства"](../extensibility/media/t5properties.png "T5Properties")  
  
2.  Добавьте следующие операторы using *TodoItem.cs* файла.  
  
    ```csharp  
    using System.ComponentModel;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  Добавление `public` модификатор доступа к объявлению класса.  
  
    ```csharp  
    public class TodoItem  
    {  
    }  
    ```  
  
     Добавьте два свойства, `Name` и `DueDate`. Мы сделаем `UpdateList()` и `CheckForErrors()` позже.  
  
    ```csharp  
    public class TodoItem  
    {  
        private TodoWindowControl parent;  
        private string name;  
        [Description("Name of the ToDo item")]  
        [Category("ToDo Fields")]  
        public string Name  
        {  
            get { return name; }  
            set  
            {  
                name = value;  
                parent.UpdateList(this);  
            }  
        }  
  
        private DateTime dueDate;  
        [Description("Due date of the ToDo item")]  
        [Category("ToDo Fields")]  
        public DateTime DueDate  
        {  
            get { return dueDate; }  
            set  
            {  
                dueDate = value;  
                parent.UpdateList(this);  
                parent.CheckForErrors();  
            }  
        }  
    }  
    ```  
  
4.  Добавьте ссылку на закрытый в пользовательский элемент управления. Добавьте конструктор, принимающий пользовательский элемент управления и имя для данного элемента списка дел. Чтобы найти значение для `daysAhead`, она возвращает свойства параметров страницы.  
  
    ```csharp  
    private TodoWindowControl parent;  
  
    public TodoItem(TodoWindowControl control, string itemName)  
    {  
        parent = control;  
        name = itemName;  
        dueDate = DateTime.Now;  
  
        double daysAhead = 0;  
        IVsPackage package = parent.parent.Package as IVsPackage;  
        if (package != null)  
        {  
            object obj;  
            package.GetAutomationObject("ToDo.General", out obj);  
  
            ToolsOptions options = obj as ToolsOptions;  
            if (options != null)  
            {  
                daysAhead = options.DaysAhead;  
            }  
        }  
  
        dueDate = dueDate.AddDays(daysAhead);  
    }  
    ```  
  
5.  Так как экземпляры `TodoItem` класса будут храниться в поле со списком и ListBox будет вызывать `ToString` функции, то необходимо перегрузить `ToString` функции. Добавьте следующий код, чтобы *TodoItem.cs*, после конструктора и до конца класса.  
  
    ```csharp  
    public override string ToString()  
    {  
        return name + " Due: " + dueDate.ToShortDateString();  
    }  
    ```  
  
6.  В *TodoWindowControl.xaml.cs*, добавьте методы-заглушки для `TodoWindowControl` класса для `CheckForError` и `UpdateList` методы. Поместите их после ProcessDialogChar и до конца файла.  
  
    ```csharp  
    public void CheckForErrors()  
    {  
    }  
    public void UpdateList(TodoItem item)  
    {  
    }  
    ```  
  
     `CheckForError` Метод будет вызывать метод с тем же именем в родительском объекте, и этот метод будет проверять, произошли ли все ошибки и их правильно обработать. `UpdateList` Метод обновляет ListBox в родительском элементе управления; метод вызывается, когда `Name` и `DueDate` свойства в ходе данного изменения класса. Они будут реализованы позже.  
  
## <a name="integrate-into-the-properties-window"></a>Интеграция в окне «Свойства»  
 Теперь напишите код, который управляет ListBox, в которой будут привязаны к **свойства** окна.  
  
 Необходимо изменить кнопки щелкните обработчик для чтения текстовое поле, создайте элемент TodoItem и добавляет его в список ListBox.  
  
1.  Замените существующий `button1_Click` функции с помощью кода, который создает нового объекта TodoItem и добавляет его в список ListBox. Он вызывает `TrackSelection()`, который будет определен позже.  
  
    ```csharp  
    private void button1_Click(object sender, RoutedEventArgs e)  
    {  
        if (textBox.Text.Length > 0)  
        {  
            var item = new TodoItem(this, textBox.Text);  
            listBox.Items.Add(item);  
            TrackSelection();  
            CheckForErrors();  
        }  
    }  
    ```  
  
2.  В режиме конструктора выберите элемент управления ListBox. В **свойства** окну, нажмите кнопку **обработчики событий** кнопку и найти **SelectionChanged** событий. Заполните текстовое поле с **listBox_SelectionChanged**. Это добавляет заглушку для обработчика SelectionChanged и присваивает его к событию.  
  
3.  Выполните метод `TrackSelection()`. Так как вам потребуется получить <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> служб, вы должны сделать <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> доступном TodoWindowControl. Добавьте следующий метод в `TodoWindow` класса:  
  
    ```  
    internal object GetVsService(Type service)  
    {  
        return GetService(service);  
    }  
    ```  
  
4.  Добавьте следующие операторы using в *TodoWindowControl.xaml.cs*:  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  Заполните обработчик SelectionChanged следующим образом:  
  
    ```  
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)  
    {  
        TrackSelection();  
    }  
    ```  
  
6.  Теперь заполните функцию TrackSelection, которая обеспечивает интеграцию с системой **свойства** окна. Эта функция вызывается, когда пользователь добавляет элемент в список или щелкает элемент в ListBox. Он добавляет содержимое ListBox SelectionContainer и передает SelectionContainer для **свойства** окна <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> обработчик событий. Служба TrackSelection отслеживает выбранные объекты в пользовательском интерфейсе (UI) и отображает их свойства  
  
    ```csharp  
    private SelectionContainer mySelContainer;  
    private System.Collections.ArrayList mySelItems;  
    private IVsWindowFrame frame = null;  
  
    private void TrackSelection()  
    {  
        if (frame == null)  
        {  
            var shell = parent.GetVsService(typeof(SVsUIShell)) as IVsUIShell;  
            if (shell != null)  
            {  
                var guidPropertyBrowser = new  
                Guid(ToolWindowGuids.PropertyBrowser);  
                shell.FindToolWindow((uint)__VSFINDTOOLWIN.FTW_fForceCreate,  
                ref guidPropertyBrowser, out frame);  
            }  
        }  
        if (frame != null)  
            {  
                frame.Show();  
            }  
        if (mySelContainer == null)  
        {  
            mySelContainer = new SelectionContainer();  
        }  
  
        mySelItems = new System.Collections.ArrayList();  
  
        var selected = listBox.SelectedItem as TodoItem;  
        if (selected != null)  
        {  
            mySelItems.Add(selected);  
        }  
  
        mySelContainer.SelectedObjects = mySelItems;  
  
        ITrackSelection track = parent.GetVsService(typeof(STrackSelection))  
                                as ITrackSelection;  
        if (track != null)  
        {  
            track.OnSelectChange(mySelContainer);  
        }  
    }  
    ```  
  
     Теперь, когда у вас есть класс, **свойства** окно можно использовать, вы можете интегрировать **свойства** окно с окном инструментов. Когда пользователь щелкает элемент в ListBox в окне инструментов **свойства** окна должны обновляться соответствующим образом. Аналогичным образом, в том случае, когда пользователь изменяет элемент в списке дел в **свойства** окна связанного элемента должны быть обновлены.  
  
7.  Теперь добавьте остальной части кода функции на обновление списка в *TodoWindowControl.xaml.cs*. Она должна удаляться и повторно добавьте измененные TodoItem из списка.  
  
    ```csharp  
    public void UpdateList(TodoItem item)  
    {  
        var index = listBox.SelectedIndex;  
        listBox.Items.RemoveAt(index);  
        listBox.Items.Insert(index, item);  
        listBox.SelectedItem = index;  
    }  
    ```  
  
8.  Тестирование кода. Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.  
  
9. Откройте **средства** > **параметры** страницы. Вы увидите категории ToDo в левой области. Категории перечислены в алфавитном порядке, поэтому перейдите в раздел служб терминалов.  
  
10. На **Todo** странице "Параметры", которые вы должны увидеть `DaysAhead` свойство значение **0**. Измените его на **2**.  
  
11. На **представления / Other Windows** откройте в меню **TodoWindow**. Тип **EndDate** в текстовое поле и нажмите кнопку **добавить**.  
  
12. В списке вы увидите два дня позже, чем текущая дата.  
  
## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Добавление текста в окне выходных данных и элементы в список задач  
 Для **список задач**, можно создать объект типа задач, а затем добавьте этот объект задачи для **список задач** путем вызова его `Add` метод. Записываемый **выходные данные** окна, вызовите его `GetPane` вызовите метод, чтобы получить объект панели, а затем `OutputString` метод объекта области.  
  
1.  В *TodoWindowControl.xaml.cs*в `button1_Click` метод, добавьте код для получения **Общие** области **вывода** окна (по умолчанию) и запись в него. Метод должен выглядеть следующим образом:  
  
    ```csharp  
    private void button1_Click(object sender, EventArgs e)  
    {  
        if (textBox.Text.Length > 0)  
        {  
            var item = new TodoItem(this, textBox.Text);  
            listBox.Items.Add(item);  
  
            var outputWindow = parent.GetVsService(  
                typeof(SVsOutputWindow)) as IVsOutputWindow;  
            IVsOutputWindowPane pane;  
            Guid guidGeneralPane = VSConstants.GUID_OutWindowGeneralPane;  
            outputWindow.GetPane(ref guidGeneralPane, out pane);  
            if (pane != null)  
            {  
                 pane.OutputString(string.Format(  
                    "To Do item created: {0}\r\n",  
                 item.ToString()));  
        }  
            TrackSelection();  
            CheckForErrors();  
        }  
    }  
    ```  
  
2.  Чтобы добавить элементы в список задач, необходимо добавить вложенный класс в класс TodoWindowControl. Вложенный класс должно быть производным от <xref:Microsoft.VisualStudio.Shell.TaskProvider>. Добавьте следующий код в конец `TodoWindowControl` класса.  
  
    ```csharp  
    [Guid("72de1eAD-a00c-4f57-bff7-57edb162d0be")]  
    public class TodoWindowTaskProvider : TaskProvider  
    {  
        public TodoWindowTaskProvider(IServiceProvider sp)  
            : base(sp)  
        {  
        }  
    }  
    ```  
  
3.  Добавьте ссылку на закрытый `TodoTaskProvider` и `CreateProvider()` метод `TodoWindowControl` класса. Код должен выглядеть следующим образом:  
  
    ```csharp  
    private TodoWindowTaskProvider taskProvider;  
    private void CreateProvider()  
    {  
        if (taskProvider == null)  
        {  
            taskProvider = new TodoWindowTaskProvider(parent);  
            taskProvider.ProviderName = "To Do";  
        }  
    }  
    ```  
  
4.  Добавить `ClearError()`, что приводит к удалению списка задач и `ReportError()`, который добавляет запись в список задач в коллекцию `TodoWindowControl` класса.  
  
    ```csharp  
    private void ClearError()  
    {  
        CreateProvider();  
        taskProvider.Tasks.Clear();  
    }  
    private void ReportError(string p)  
    {  
        CreateProvider();  
        var errorTask = new Task();  
        errorTask.CanDelete = false;  
        errorTask.Category = TaskCategory.Comments;  
        errorTask.Text = p;  
  
        taskProvider.Tasks.Add(errorTask);  
  
        taskProvider.Show();  
  
        var taskList = parent.GetVsService(typeof(SVsTaskList))  
            as IVsTaskList2;  
        if (taskList == null)  
        {  
            return;  
        }  
  
        var guidProvider = typeof(TodoWindowTaskProvider).GUID;  
         taskList.SetActiveProvider(ref guidProvider);  
    }  
    ```  
  
5.  Теперь реализуйте `CheckForErrors` метода, как показано ниже.  
  
    ```csharp  
    public void CheckForErrors()  
    {  
        foreach (TodoItem item in listBox.Items)  
        {  
            if (item.DueDate < DateTime.Now)  
            {  
                ReportError("To Do Item is out of date: "  
                    + item.ToString());  
            }  
        }  
    }  
    ```  
  
## <a name="try-it-out"></a>Попробовать  
  
1.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.  
  
2.  Откройте **TodoWindow** (**представление** > **другие Windows** > **TodoWindow**).  
  
3.  Введите в текстовом поле и нажмите кнопку **добавить**.  
  
     Срок 2 дней, после добавления сегодня в поле со списком. Ошибки не создаются и **список задач** (**представление** > **список задач**) следует нет записей.  
  
4.  Теперь измените параметр на **средства** > **параметры** > **ToDo** странице из **2** к **0**.  
  
5.  Введите еще что-нибудь **TodoWindow** и нажмите кнопку **добавить** еще раз. Это вызывает ошибку, а также запись в **список задач**.  
  
     При добавлении элементов, Начальная дата будет присвоено теперь плюс 2 дня.  
  
6.  На **представление** меню, нажмите кнопку **выходные данные** открыть **вывода** окна.  
  
     Обратите внимание, что каждый раз, нужно добавить элемент, сообщение отображается в **список задач** области.  
  
7.  Щелкните один из элементов в поле со списком.  
  
     **Свойства** окне отображаются два свойства для элемента.  
  
8.  Изменить одно из свойств и нажмите клавишу **ввод**.  
  
     Элемент обновляется в поле со списком.