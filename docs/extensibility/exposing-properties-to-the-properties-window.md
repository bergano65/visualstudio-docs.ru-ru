---
title: "Предоставление доступа к свойствам в окне &#171;Свойства&#187; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "свойства [Visual Studio SDK] предоставление в обозревателе свойств"
  - "свойства [Visual Studio SDK]"
  - "Обозреватель свойств, предоставление доступа к свойствам"
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
caps.latest.revision: 36
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 36
---
# Предоставление доступа к свойствам в окне &#171;Свойства&#187;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В этом пошаговом руководстве предоставляет открытые свойства объекта **Свойства** окна. Изменения, внесенные в эти свойства, отражаются в **Свойства** окна.  
  
## Обязательные компоненты  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Для получения дополнительной информации см. [Установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Предоставление доступа к свойствам в окне «Свойства»  
 В этом разделе Создание пользовательского окна инструментов и отобразить открытые свойства объекта области связанное окно в **Свойства** окна.  
  
#### Экспорт свойств в окне «Свойства»  
  
1.  Все расширения Visual Studio начинается с развертывания проект VSIX, который будет содержать средств расширения. Создание [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проект VSIX с именем `MyObjectPropertiesExtension`. Можно найти шаблон проекта VSIX в **Новый проект** диалоговом окне под **Visual C\# и расширяемость**.  
  
2.  Добавление окна инструментов путем добавления пользовательского окна инструментов шаблон элемента с именем `MyToolWindow`. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **Добавить или создать элемент**. В **диалоговое окно Добавление нового элемента**, последовательно выберите пункты **элементы Visual C\# и расширяемость** и выберите **настраиваемое окно инструмента**. В **имя** в нижней части диалогового окна, измените имя файла `MyToolWindow.cs`. Дополнительные сведения о создании пользовательского окна инструментов см. в разделе [Создание расширения с помощью окна инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  Откройте MyToolWindow.cs и добавьте следующий оператор using:  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4.  Теперь добавьте следующие поля в `MyToolWindow` класса.  
  
    ```c#  
    private ITrackSelection trackSel;  
    private SelectionContainer selContainer;  
  
    ```  
  
5.  Добавьте следующий код в класс MyToolWindow.  
  
    ```c#  
    private ITrackSelection TrackSelection  
    {  
        get  
        {  
            if (trackSel == null)  
                trackSel =  
                   GetService(typeof(STrackSelection)) as ITrackSelection;  
            return trackSel;  
        }  
    }  
  
    public void UpdateSelection()  
    {  
        ITrackSelection track = TrackSelection;  
        if (track != null)  
            track.OnSelectChange((ISelectionContainer)selContainer);  
    }  
  
    public void SelectList(ArrayList list)  
    {  
        selContainer = new SelectionContainer(true, false);  
        selContainer.SelectableObjects = list;  
        selContainer.SelectedObjects = list;  
        UpdateSelection();  
    }  
  
    public override void OnToolWindowCreated()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
     `TrackSelection` Использует свойство `GetService` для получения `STrackSelection` службы, которая предоставляет <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> интерфейса.`OnToolWindowCreated` Обработчик событий и `SelectList` метод образуют список выбранных объектов, содержащий только средство окна области сам объект.`UpdateSelection` Указывает метод **Свойства** окно, чтобы отобразить открытые свойства на панели инструментов окна.  
  
6.  Выполните сборку решения и запустите отладку. Должна появиться экспериментальном экземпляре Visual Studio.  
  
7.  Если **Свойства** окно не отображается, откройте ее, нажав клавишу F4.  
  
8.  Откройте **MyToolWindow** окна. Его можно найти в **представления и другие окна**.  
  
     Открывается окно и открытые свойства области окна в **Свойства** окна.  
  
9. Изменение **заголовок** свойство в **Свойства** окна **Мои свойства объекта**.  
  
     Заголовок окна MyToolWindow изменяется соответствующим образом.  
  
## Предоставление доступа к свойствам окна инструментов  
 В этом разделе добавьте окна инструментов и предоставлять его свойства. Изменения свойств отражаются в **Свойства** окна.  
  
#### Чтобы предоставить свойства окна инструментов  
  
1.  Откройте MyToolWindow.cs и добавьте в класс MyToolWindow открытый логическое свойство IsChecked.  
  
    ```c#  
    [Category("My Properties")]  
    [Description("MyToolWindowControl properties")]  
    public bool IsChecked  
    {  
        get {  
            if (base.Content == null)  return false;  
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;   
        }  
        set {  
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;  
        }  
    }  
    ```  
  
     Это свойство получает свое состояние установки флажка WPF, который будет создан позже.  
  
2.  Откройте MyToolWindowControl.xaml.cs и замените следующий код в конструктор MyToolWindowControl.  
  
    ```vb  
    private MyToolWindow pane;  
    public MyToolWindowControl(MyToolWindow pane)  
    {  
        InitializeComponent();  
        this.pane = pane;  
        checkBox.IsChecked = false;  
    }  
    ```  
  
     Это дает `MyToolWindowControl` доступ к `MyToolWindow` области.  
  
3.  В MyToolWindow.cs, измените `MyToolWindow` Конструктор следующим образом:  
  
    ```c#  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4.  Изменить режим конструктора MyToolWindowControl.  
  
5.  Кнопка «Удалить» и добавить флажок из **элементов** в левом верхнем углу.  
  
6.  Добавьте Checked и Unchecked события. Установите флажок в режиме конструктора. В **Свойства** окно, нажмите кнопку обработчики событий \(в верхней правой части **Свойства** окна\). Найти **Checked** и тип **checkbox\_Checked** в текстовом поле Найти **Unchecked** и тип **checkbox\_Unchecked** в текстовом поле.  
  
7.  Добавление обработчиков событий флажок:  
  
    ```c#  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = true;  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.UpdateSelection();  
    }  
    ```  
  
8.  Выполните сборку решения и запустите отладку.  
  
9. В экспериментальном экземпляре откройте **MyToolWindow** окна.  
  
     Ищите окна свойств в **Свойства** окна.**IsChecked** свойство отображается в нижней части окна, в разделе **Свойства: Мой** категории.  
  
10. Установите флажок **MyToolWindow** окна.**IsChecked** в **Свойства** примет вид окна **True**. Снимите флажок в **MyToolWindow** окна.**IsChecked** в **Свойства** примет вид окна **False**. Измените значение **IsChecked** в **Свойства** окна. Флажок в **MyToolWindow** окна изменяется в соответствии с новым значением.  
  
    > [!NOTE]
    >  Если необходимо уничтожить объект, который отображается в **Свойства** окно, вызов `OnSelectChange` с `null` контейнера выделения первой. После удаления свойства или объекта, можно изменить выбор контейнер, который обновил <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> и <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> список.  
  
## Изменение списков выбора  
 В этом разделе добавьте список выбора для основных свойств класса и используйте интерфейс окна инструментов, чтобы выбрать список выбора для отображения.  
  
#### Для изменения списков выбора  
  
1.  Откройте MyToolWindow.cs и добавьте открытый класс с именем `Simple`.  
  
    ```c#  
    public class Simple  
    {  
        private string someText = "";  
  
        [Category("My Properties")]  
        [Description("Simple Properties")]  
        [DisplayName("My Text")]  
        public string SomeText  
        {  
            get { return someText; }  
            set { someText = value; }  
        }  
  
        [Category("My Properties")]  
        [Description("Read-only property")]  
        public bool ReadOnly  
        {  
            get { return false; }  
        }  
    }  
    ```  
  
2.  Добавьте свойство SimpleObject класса MyToolWindow, а также два метода для переключения **Свойства** окно выбора между область окна и `Simple` объекта.  
  
    ```c#  
    private Simple simpleObject = null;  
    public Simple SimpleObject  
    {  
        get  
        {  
            if (simpleObject == null) simpleObject = new Simple();  
            return simpleObject;  
        }  
    }  
  
    public void SelectSimpleList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(SimpleObject);  
        SelectList(listObjects);  
    }  
  
    public void SelectThisList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
3.  Замените обработчики флажок в MyToolWindowControl.cs, следующие строки кода:  
  
    ```c#  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
     {  
        pane.IsChecked = true;  
        pane.SelectSimpleList();  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.SelectThisList();  
        pane.UpdateSelection();  
    }  
    ```  
  
4.  Выполните сборку решения и запустите отладку.  
  
5.  В экспериментальном экземпляре откройте **MyToolWindow** окна.  
  
6.  Установите флажок в **MyToolWindow** окна.**Свойства** окно отображает `Simple` объект свойства, **SomeText** и **ReadOnly**. Снимите флажок. Открытые свойства окна отображаются в **Свойства** окна.  
  
    > [!NOTE]
    >  Отображаемое имя **SomeText** — **текст моего**.  
  
## Рекомендации  
 В этом пошаговом руководстве <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> реализуется так, доступный для выбора объект коллекции и коллекции выбранных объектов одной коллекции. В списке обозревателя свойств отображается только выбранный объект. Для более полной реализации ISelectionContainer просмотрите примеры Reference.ToolWindow.  
  
 Окна инструментов Visual Studio сохраняются между сеансами Visual Studio. Дополнительные сведения на сохранение состояния окна инструментов в разделе <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## См. также  
 [Расширение свойств и окна свойств](../extensibility/extending-properties-and-the-property-window.md)