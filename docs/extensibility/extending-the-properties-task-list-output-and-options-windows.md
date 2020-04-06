---
title: Расширить свойства, список задач, выход, окна опций
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db14068c97ff6868f5fb73c9ddd790020e99e7c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711637"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>Расширить окна свойств, задач, выходных данных и вариантов
Вы можете получить доступ к любому окну инструмента в Visual Studio. В этом пошаговом показании, как интегрировать информацию о окне инструмента в новую страницу **Options** и новую настройку на странице **Свойств,** а также как писать в **список задач** и окна **вывода.**

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-an-extension-with-a-tool-window"></a>Создание расширения с окном инструмента

1. Создайте проект под названием **TodoList** с помощью шаблона VSIX и добавьте шаблон пользовательского окна инструмента под названием **TodoWindow.**

    > [!NOTE]
    > Для получения дополнительной информации о создании расширения с окном инструмента [см. Создать расширение с окном инструмента.](../extensibility/creating-an-extension-with-a-tool-window.md)

## <a name="set-up-the-tool-window"></a>Настройка окна инструмента
 Добавьте TextBox, в котором можно ввести новый элемент ToDo, кнопку для добавления нового элемента в список и ListBox для отображения элементов в списке.

1. В *TodoWindow.xaml*удалите элементы управления Button, TextBox и StackPanel из userControl.

    > [!NOTE]
    > Это не удаляет **обработчик событий button1_Click,** который вы будете повторно использовать на более позднем этапе.

2. Из раздела **All WPF Controls** в **наборе инструментов**перетащите элемент управления **canvas** в сетку.

3. Перетащите **TextBox**, **кнопку**, и **ListBox** на холст. Упорядочить элементы так, чтобы TextBox и кнопка находятся на том же уровне, и ListBox заполняет остальную часть окна под ними, как на рисунке ниже.

     ![Окно завершенных инструментов.](../extensibility/media/t5-toolwindow.png "T5-ToolWindow")

4. В панели XAML найдите кнопку и установите свойство содержимого для **добавления.** Переподключение обработчика событий кнопки `Click="button1_Click"` к управлению кнопкой, добавив атрибут. Блок Canvas должен выглядеть следующим образом:

    ```xml
    <Canvas HorizontalAlignment="Left" Width="306">
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>
    </Canvas>
    ```

### <a name="customize-the-constructor"></a>Настройка конструктора

1. В *TodoWindowControl.xaml.cs* файле добавьте следующую директиву с помощью:

    ```csharp
    using System;
    ```

2. Добавьте общедоступную ссылку на TodoWindow и поите, чтобы конструктор TodoWindowControl взял параметр TodoWindow. Код должен выглядеть следующим образом:

    ```csharp
    public TodoWindow parent;

    public TodoWindowControl(TodoWindow window)
    {
        InitializeComponent();
        parent = window;
    }
    ```

3. В *TodoWindow.cs,* измените конструктор TodoWindowControl, чтобы включить параметр TodoWindow. Код должен выглядеть следующим образом:

    ```csharp
    public TodoWindow() : base(null)
    {
        this.Caption = "TodoWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;

         this.Content = new TodoWindowControl(this);
    }
    ```

## <a name="create-an-options-page"></a>Создание страницы опционов
 Вы можете предоставить страницу в диалоговом поле **Options,** чтобы пользователи могли изменять настройки для окна инструмента. Для создания страницы Options требуется как класс, описывающий параметры, так и запись в *TodoListPackage.cs* или *файлtoListPackage.vb.*

1. Добавьте класс с именем `ToolsOptions.cs`. Сделать `ToolsOptions` класс <xref:Microsoft.VisualStudio.Shell.DialogPage>наследовать от .

   ```csharp
   class ToolsOptions : DialogPage
   {
   }
   ```

2. Добавьте следующую директиву using:

   ```csharp
   using Microsoft.VisualStudio.Shell;
   ```

3. Страница Options в этом пошаговом листе предоставляет только один вариант под названием DaysAhead. Добавьте в `ToolsOptions` класс частное поле под названием **DaysAhead** и свойство под названием **DaysAhead:**

   ```csharp
   private double daysAhead;

   public double DaysAhead
   {
       get { return daysAhead; }
       set { daysAhead = value; }
   }
   ```

   Теперь вы должны сделать проект осведомлены об этой странице Параметры.

### <a name="make-the-options-page-available-to-users"></a>Сделать страницу «Параметры» доступной для пользователей

1. В *TodoWindowPackage.cs,* <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> добавьте `TodoWindowPackage` в класс:

    ```csharp
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]
    ```

2. Первым параметром конструктора ProvideOptionPage является тип `ToolsOptions`класса, который вы создали ранее. Второй параметр, "ToDo", это название категории в поле диалога **Опционов.** Третий параметр, "Общий", это название подкатегории диалогового окна **Options,** где будет доступна страница Options. Следующие два параметра являются имитными ими ресурсов для строк; во-первых, это название категории, а во-вторых, название подкатегории. Окончательный параметр определяет, можно ли получить доступ к этой странице с помощью автоматизации.

     Когда пользователь открывает страницу Options, она должна напоминать следующую картинку.

     ![Страница вариантов](../extensibility/media/t5optionspage.gif "T5OptionsPage")

     Обратите внимание на категорию **ToDo** и подкатегорию **General**.

## <a name="make-data-available-to-the-properties-window"></a>Сделать данные доступными для окна Свойств
 Вы можете сделать информацию списка ToDo доступной, создав класс с именем, `TodoItem` который хранит информацию об отдельных элементах в списке ToDo.

1. Добавьте класс с именем `TodoItem.cs`.

     Когда окно инструмента будет доступно пользователям, элементы в ListBox будут представлены TodoItems. Когда пользователь выбирает один из этих элементов в ListBox, в окне **Свойств** будет отображаться информация о товаре.

     Чтобы сделать данные доступными в окне **свойств,** вы превращаете `Description` `Category`данные в общедоступные свойства, которые имеют два специальных атрибута, и . `Description`— это текст, который отображается в нижней части окна **Свойств.** `Category`определяет, где должно отображаться свойство при отображении окна **Свойств** в **представлении Категоризированные.** На следующем рисунке окно **Свойства** находится в **категоризированном** представлении, выбрано свойство **имени** в категории **ToDo Fields,** а описание свойства **«Имя»** отображается в нижней части окна.

     ![Окно свойств](../extensibility/media/t5properties.png "T5Свойства")

2. Добавьте следующие *директивы,* TodoItem.cs файл.

    ```csharp
    using System.ComponentModel;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Добавьте `public` модификатор доступа в объявление класса.

    ```csharp
    public class TodoItem
    {
    }
    ```

     Добавить два `Name` свойства, и `DueDate`. Мы сделаем `UpdateList()` и `CheckForErrors()` позже.

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

4. Добавьте приватную ссылку на пользовательский контроль. Добавьте конструктор, который берет элемент пользователя и имя для этого элемента ToDo. Чтобы найти значение `daysAhead`для, он получает свойство страницы Options.

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

5. Поскольку экземпляры `TodoItem` класса будут храниться в ListBox и `ToString` ListBox вызовет функцию, необходимо перегрузить функцию. `ToString` Добавьте следующий код *в TodoItem.cs,* после конструктора и до конца класса.

    ```csharp
    public override string ToString()
    {
        return name + " Due: " + dueDate.ToShortDateString();
    }
    ```

6. В *TodoWindowControl.xaml.cs,* добавить заглушки методы `TodoWindowControl` класса `CheckForError` и `UpdateList` методы. Положите их после ProcessDialogChar и до конца файла.

    ```csharp
    public void CheckForErrors()
    {
    }
    public void UpdateList(TodoItem item)
    {
    }
    ```

     Метод `CheckForError` вызовет метод с одинаковым именем в родительском объекте, и этот метод проверит, были ли ошибки, и правильно с ними обработает. Метод `UpdateList` обновит ListBox в родительском элементе; метод вызывается при `Name` `DueDate` изменении свойств в этом классе. Они будут реализованы позже.

## <a name="integrate-into-the-properties-window"></a>Интеграция в окно Свойств
 Теперь напишите код, который управляет ListBox, который будет привязан к окну **Свойств.**

 Необходимо изменить обработчик кнопки, чтобы прочитать TextBox, создать TodoItem и добавить его в ListBox.

1. Замените `button1_Click` существующую функцию кодом, который создает новый TodoItem и добавляет ее в ListBox. Он `TrackSelection()`вызывает, который будет определен позже.

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

2. В представлении Design выберите элемент управления ListBox. В окне **Свойства** щелкните кнопку **обработчиков событий** и найдите событие **SelectionChanged.** Заполните текстовую коробку с **listBox_SelectionChanged**. Это добавляет заглушку для обработчика SelectionChanged и назначает ее событию.

3. Выполните метод `TrackSelection()`. Так как вам нужно <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> будет получить услуги, вам нужно сделать <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> доступным todoWindowControl. Добавьте в класс `TodoWindow` следующий метод:

    ```
    internal object GetVsService(Type service)
    {
        return GetService(service);
    }
    ```

4. Добавьте следующие директивы с помощью *TodoWindowControl.xaml.cs:*

    ```csharp
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Shell.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    ```

5. Заполните обработчик SelectionChanged следующим образом:

    ```
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        TrackSelection();
    }
    ```

6. Теперь заполните функцию TrackSelection, которая обеспечит интеграцию с окном **Properties.** Эта функция вызывается, когда пользователь добавляет элемент в ListBox или нажимает на элемент в ListBox. Он добавляет содержимое ListBox в SelectionContainer и передает SelectionContainer обработчику <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> событий окна **Properties.** Служба TrackSelection отслеживает выбранные объекты в пользовательском интерфейсе (UI) и отображает их свойства

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

     Теперь, когда у вас есть класс, который может использовать окно **Свойств,** можно интегрировать окно **Свойств** с окном инструмента. Когда пользователь нажимает элемент в Листбоксе в окне инструмента, окно **Свойств** должно быть соответствующим образом обновлено. Аналогичным образом, при изменении элемента ToDo в окне **свойств** необходимо обновить связанный элемент.

7. Теперь добавьте остальную часть кода функции UpdateList в *TodoWindowControl.xaml.cs*. Он должен упасть и повторно добавить модифицированный TodoItem из ListBox.

    ```csharp
    public void UpdateList(TodoItem item)
    {
        var index = listBox.SelectedIndex;
        listBox.Items.RemoveAt(index);
        listBox.Items.Insert(index, item);
        listBox.SelectedItem = index;
    }
    ```

8. Проверьте свой код. Выполните сборку решения и запустите отладку. Экспериментальный экземпляр должен появиться.

9. Откройте страницу **«Параметры** **инструментов».** >  Вы должны увидеть категорию ToDo в левом стеле. Категории перечислены в алфавитном порядке, так что посмотрите под Ts.

10. На странице опций **Todo** следует `DaysAhead` увидеть набор свойств до **0**. Измените его на **2**.

11. В **представлении / Другое** меню Windows, откройте **TodoWindow**. Введите **EndDate** в текстовом поле и нажмите **Добавить**.

12. В поле списка вы должны увидеть дату на два дня позже, чем сегодня.

## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Добавление текста в окно вывода и элементов в список задач
 Для **списка задач**вы создаете новый объект задачи типа, а затем добавляете `Add` объект задачи в **список задач,** вызывая его метод. Чтобы написать в окно **вывода,** вы называете его `GetPane` метод для `OutputString` получения объекта панели, а затем вы называете метод объекта панели.

1. В *TodoWindowControl.xaml.cs*, `button1_Click` в методе добавьте код, чтобы получить **общее** стекло окна **вывода** (которое является по умолчанию), и написать на него. Метод будет выглядеть так:

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

2. Чтобы добавить элементы в список задач, необходимо добавить вложенный класс в класс TodoWindowControl. Вложенный класс должен вытекать из <xref:Microsoft.VisualStudio.Shell.TaskProvider>. Добавьте следующий код в `TodoWindowControl` конец класса.

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

3. Затем добавьте приватную `CreateProvider()` ссылку `TodoWindowControl` `TodoTaskProvider` на класс и метод. Код должен выглядеть следующим образом:

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

4. Добавить, `ClearError()`который очищает список `ReportError()`задач, и , который добавляет `TodoWindowControl` запись в список задач, в класс.

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

5. Теперь `CheckForErrors` реализуем метод следующим образом.

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

## <a name="try-it-out"></a>Попробуйте продукт

1. Выполните сборку решения и запустите отладку. Появляется экспериментальный экземпляр.

2. Откройте **TodoWindow** **(Посмотреть** > **другие Windows** > **TodoWindow**).

3. Введите что-то в текстовом поле, а затем нажмите **Добавить**.

     Срок одолжения через 2 дня после сегодняшнего дня добавляется в поле списка. Ошибки не генерируются, и **список задач** **(Список** > **задач)** не должен иметь записей.

4. Теперь измените настройку на странице **2** Параметры **инструментов** > **Options** > **ToDo** с 2 назад на **0.**

5. Введите что-то еще в **TodoWindow,** а затем нажмите **Добавить** еще раз. Это вызывает ошибку, а также запись в **списке задач.**

     При добавлении элементов начальная дата установлена до плюс 2 дня.

6. В меню **«Посмотреть»** нажмите **«Выход»,** чтобы открыть окно **вывода.**

     Обратите внимание, что каждый раз, когда вы добавляете элемент, сообщение отображается в панели **списка задач.**

7. Нажмите на один из элементов listBox.

     Окно **Свойства** отображает два свойства для элемента.

8. Измените одно из свойств, а затем нажмите **Enter.**

     Элемент обновляется в ListBox.
