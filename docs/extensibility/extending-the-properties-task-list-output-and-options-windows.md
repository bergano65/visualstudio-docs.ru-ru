---
title: Расширение свойств, список задач, выходные данные и параметры Windows | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4db9bb9101bd06921814132856fab0335a4a2530
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="extending-the-properties-task-list-output-and-options-windows"></a>Расширение свойств, список задач, выходные данные и параметры Windows
Можно получить доступ к любого окна инструментов в Visual Studio. В этом пошаговом руководстве показано, как интегрировать сведения о окна инструментов в новый **параметры** страницы и новый параметр на **свойства** страницы, а также способ записи **список задач** и **вывода** windows.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-an-extension-with-a-tool-window"></a>Создайте расширение с окном инструментов  
  
1.  Создайте проект с именем **TodoList** с помощью шаблона VSIX и добавить шаблон элемента окна пользовательского инструмента с именем **TodoWindow**.  
  
    > [!NOTE]
    >  Дополнительные сведения о создании модуля с окном инструментов см. в разделе [создания расширения с окном инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="set-up-the-tool-window"></a>Настройка окна инструментов  
 Текстовое поле для ввода нового элемента ToDo, кнопку, чтобы добавить новый элемент в списке и ListBox для отображения элементов в списке.  
  
1.  В TodoWindow.xaml удалите элементы управления кнопки, текстового поля и StackPanel из пользовательского элемента управления.  
  
    > [!NOTE]
    >  Это действие не удаляет **button1_Click** обработчик событий, который будет использовать в дальнейшем.  
  
2.  Из **всех элементов управления WPF** раздел **элементов**, перетащите **холст** элемента управления в сетке.  
  
3.  Перетащите **TextBox**, **кнопку**и **ListBox** на холст. Упорядочивание элементов так, чтобы текстовое поле и кнопку на том же уровне и ListBox заполняет остальную часть окна под ними, как показано на рисунке ниже.  
  
     ![Окно инструментов завершения](../extensibility/media/t5-toolwindow.png "окно инструментов T5")  
  
4.  На панели XAML поиск кнопки и установите его свойство содержимого **добавить**. Подключите обработчик события для кнопки в элемент управления Button, добавив `Click="button1_Click"` атрибута. Холст Блок должен выглядеть следующим образом:  
  
    ```xml  
    <Canvas HorizontalAlignment="Left" Width="306">  
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>  
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>  
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>  
    </Canvas>  
    ```  
  
#### <a name="customize-the-constructor"></a>Настройка конструктора  
  
1.  В файле TodoWindowControl.xaml.cs добавьте следующие инструкции с помощью:  
  
    ```csharp  
    using System;  
    ```  
  
2.  Добавьте открытый ссылку на TodoWindow и принимать параметр TodoWindow конструктор TodoWindowControl. Код должен выглядеть следующим образом:  
  
    ```csharp  
    public TodoWindow parent;  
  
    public TodoWindowControl(TodoWindow window)  
    {  
        InitializeComponent();  
        parent = window;  
    }  
    ```  
  
3.  В TodoWindow.cs измените конструктор TodoWindowControl необходимо добавить параметр TodoWindow. Код должен выглядеть следующим образом:  
  
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
 Можно указать страницу в **параметры** диалоговое окно, чтобы пользователи могут изменять параметры для окна инструментов. Создание страницы параметров требует как класс, который описывает параметры и запись в файле TodoListPackage.cs или TodoListPackage.vb.  
  
1.  Добавьте класс с именем `ToolsOptions.cs`. Сделайте ToolsOptions класс наследовал от <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
    ```csharp  
    class ToolsOptions : DialogPage  
    {  
    }  
    ```  
  
2.  Добавьте следующий код с помощью инструкции:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
3.  На странице параметры в этом пошаговом руководстве содержится только один параметр под названием DaysAhead. Добавьте закрытое поле с именем **daysAhead** и свойство с именем **DaysAhead** ToolsOptions класс:  
  
    ```csharp  
    private double daysAhead;  
  
    public double DaysAhead  
    {  
        get { return daysAhead; }  
        set { daysAhead = value; }  
    }  
    ```  
  
 Теперь необходимо проверить проекта помнить о странице "Параметры".  
  
#### <a name="make-the-options-page-available-to-users"></a>Доступность для пользователей страницы параметров  
  
1.  Добавьте в TodoWindowPackage.cs, <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> TodoWindowPackage класс:  
  
    ```csharp  
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]  
    ```  
  
2.  Первый параметр в конструктор ProvideOptionPage является типом класса ToolsOptions, которая была создана ранее. Второй параметр «ToDo» является имя категории в **параметры** диалоговое окно. Третий параметр «Общие» — это имя подкатегории **параметры** диалоговое окно «», где будут доступны страницы параметров. Следующие два параметра являются идентификаторы ресурсов для строки; Первый аргумент — имя категории, а второй — это имя подкатегории. Последний параметр определяет, может ли доступ к этой странице с помощью автоматизации.  
  
     Когда пользователь открывает страницу параметров, она должна иметь вид следующий рисунок.  
  
     ![Страница «Параметры»](../extensibility/media/t5optionspage.gif "T5OptionsPage")  
  
     Обратите внимание, категории **ToDo** и подкатегорию **Общие**.  
  
## <a name="make-data-available-to-the-properties-window"></a>Сделать данные доступными в окне «Свойства»  
 Чтобы сделать сведения о списке можно сделать доступными, создав класс с именем TodoItem, хранящего сведения об отдельных элементов в списке ToDo.  
  
1.  Добавьте класс с именем `TodoItem.cs`.  
  
     Когда окно средства доступны пользователям, позиции в списке представлен TodoItems. Когда пользователь выбирает один из этих элементов в поле со списком **свойства** окне будут отображаться сведения об элементе.  
  
     Чтобы сделать данные доступными в **свойства** окна, данные превратить в открытых свойств, которые имеют две специальные атрибуты `Description` и `Category`. `Description` Представляет текст, отображаемый в нижней части **свойства** окна. `Category` Определяет, где свойство должно выглядеть при **свойства** откроется окно в **по категориям** представления. На следующем рисунке **свойства** окно находится в **по категориям** представление, **имя** свойство в **поля ToDo** категории флажок установлен и описание **имя** свойство отображается в нижней части окна.  
  
     ![Окно "Свойства"](../extensibility/media/t5properties.png "T5Properties")  
  
2.  Добавьте следующий код с помощью инструкций TodoItem.cs файла.  
  
    ```csharp  
    using System.ComponentModel;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  Добавить `public` модификатор доступа к объявлению класса.  
  
    ```csharp  
    public class TodoItem  
    {  
    }  
    ```  
  
     Добавьте два свойства, имя и DueDate. Мы сделаем это UpdateList() и CheckForErrors() позже.  
  
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
  
4.  Добавьте закрытый ссылку на пользовательский элемент управления. Добавьте конструктор, который принимает пользовательский элемент управления и имя для этого элемента ToDo. Чтобы найти значение daysAhead, она возвращает свойства параметров страницы.  
  
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
  
5.  Так как экземпляры `TodoItem` класса будут храниться в поле со списком и поле со списком будет вызывать `ToString` функция, то необходимо перегрузить `ToString` функции. Добавьте следующий код к TodoItem.cs, после конструктора и до конца класса.  
  
    ```csharp  
    public override string ToString()  
    {  
        return name + " Due: " + dueDate.ToShortDateString();  
    }  
    ```  
  
6.  В TodoWindowControl.xaml.cs, добавьте методы-заглушки в класс TodoWindowControl `CheckForError` и `UpdateList` методы. Поместите их после ProcessDialogChar и до конца файла.  
  
    ```csharp  
    public void CheckForErrors()  
    {  
    }  
    public void UpdateList(TodoItem item)  
    {  
    }  
    ```  
  
     `CheckForError` Метод будет вызывать метод с тем же именем в родительском объекте, и этот метод проверяет ли все ошибки, произошедшие и правильно обработать. `UpdateList` Метод происходит обновление ListBox в родительском элементе управления, когда вызывается метод `Name` и `DueDate` свойства в это изменение класса. Они будут реализованы позже.  
  
## <a name="integrate-into-the-properties-window"></a>Интеграция в окне «Свойства»  
 Напишите код, который управляет ListBox, который будет привязан к **свойства** окна.  
  
 Необходимо изменить кнопки выберите обработчик для чтения текстовое поле, создания TodoItem и добавляет его в поле со списком.  
  
1.  Заменить существующий `button1_Click` функция с кодом, который создает новый TodoItem и добавляет его в поле со списком. Он вызывает TrackSelection(), которые будут определены позже.  
  
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
  
2.  В режиме конструктора выберите элемент управления ListBox. В **свойства** окну, нажмите кнопку **обработчики событий** кнопку и найдите событие SelectionChanged. Заполнить текстовое поле с **listBox_SelectionChanged**. Это добавляет заглушку для обработчика SelectionChanged и присваивает его к событию.  
  
3.  Реализуйте метод TrackSelection(). Так как вам потребуется получить <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> службы, необходимо сделать <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> TodoWindowControl доступны. Добавьте следующий метод в класс TodoWindow:  
  
    ```  
    internal object GetVsService(Type service)  
    {  
        return GetService(service);  
    }  
    ```  
  
4.  Добавьте следующие операторы using в TodoWindowControl.xaml.cs:  
  
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
  
6.  Теперь заполните функцию TrackSelection, которая будет обеспечивают интеграцию с **свойства** окна. Эта функция вызывается, когда пользователь добавляет элемент в список или щелкает элемент в поле со списком. Он добавляет содержимое в раскрывающемся списке SelectionContainer и передает SelectionContainer для **свойства** окна <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> обработчика событий. Служба TrackSelection отслеживает выбранных объектов в пользовательском интерфейсе (UI) и отобразит их свойств  
  
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
  
     Теперь, когда класс, **свойства** окно можно использовать, вы можете интегрировать **свойства** окно с окном инструментов. Когда пользователь щелкает элемент в поле со списком в окне инструментов **свойства** окна должны обновляться соответствующим образом. Аналогичным образом, в том случае, когда пользователь изменяет элемент ToDo в **свойства** окна связанного элемента должны быть обновлены.  
  
7.  Теперь добавьте остальная часть кода функции на обновление списка в TodoWindowControl.xaml.cs. Его необходимо удалить и повторно добавить измененный TodoItem из списка.  
  
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
  
9. Откройте **Сервис / Параметры** страниц. Вы увидите категории ToDo в левой области. Категории перечислены в алфавитном порядке, так что ищите в разделе служб терминалов.  
  
10. На странице параметров Todo, вы увидите DaysAhead набора свойств, к **0**. Измените его на **2**.  
  
11. Для представления и другие окна выберите пункт **TodoWindow**. Тип **EndDate** в текстовом поле и нажмите кнопку **добавить**.  
  
12. В списке вы увидите двух дней позднее текущей даты.  
  
## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Добавление текста в окне вывода и элементы в списке задач  
 Для **список задач**, можно создать новый объект типа "Задача", а затем добавьте этот объект задачи для **список задач** путем вызова метода Add. Для записи **вывода** вызвать его getpane-метод для получения объекта области и затем вызвать метод OutputString объекта области.  
  
1.  В TodoWindowControl.xaml.cs в `button1_Click` метод, добавьте код для получения **Общие** области **вывода** окна (это значение по умолчанию) и для записи. Метод должен выглядеть следующим образом:  
  
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
  
2.  Чтобы добавить элементы в список задач, необходимо добавить вложенный класс TodoWindowControl класс. Вложенный класс должен быть производным от <xref:Microsoft.VisualStudio.Shell.TaskProvider>. Добавьте следующий код в конец TodoWindowControl класса.  
  
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
  
3.  Далее добавьте закрытый ссылку на TodoTaskProvider и CreateProvider() метод к классу TodoWindowControl. Код должен выглядеть следующим образом:  
  
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
  
4.  Добавьте в класс TodoWindowControl ClearError(), который очищает список задач, и ReportError(), который добавляет запись в список задач.  
  
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
  
5.  Реализуйте метод CheckForErrors следующим образом.  
  
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
  
## <a name="trying-it-out"></a>Проверки применимости  
  
1.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.  
  
2.  Откройте TodoWindow (**представления и других окон или TodoWindow**).  
  
3.  Введите в текстовом поле и нажмите кнопку **добавить**.  
  
     Срок 2 дней после текущей добавляется в список. Ошибки не создаются и **список задач** (**Просмотр / задач список**) должен иметь нет записей.  
  
4.  Теперь измените параметр на **Сервис / Параметры / ToDo** страницу **2** к **0**.  
  
5.  Введите еще что-нибудь **TodoWindow** и нажмите кнопку **добавить** еще раз. Это вызывает ошибку, а также запись в **списка задач**.  
  
     При добавлении элементов начальной даты устанавливается теперь плюс 2 дня.  
  
6.  На **представление** меню, нажмите кнопку **выходные данные** Открытие **вывода** окна.  
  
     Обратите внимание, что каждый раз, нужно добавить элемент, сообщение отображается в **список задач** области.  
  
7.  Выберите один из элементов в поле со списком.  
  
     **Свойства** выводятся два свойства для элемента.  
  
8.  Измените одно из свойств и нажмите клавишу ВВОД.  
  
     Чтобы обновить элемент, в поле со списком.