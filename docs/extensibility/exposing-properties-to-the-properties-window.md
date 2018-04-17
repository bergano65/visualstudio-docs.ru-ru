---
title: Предоставление доступа к свойствам в окне «Свойства» | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 12dcb30374250ca7aa917cf19b3a01ba57862c6d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="exposing-properties-to-the-properties-window"></a>Предоставление доступа к свойствам в окне «Свойства»
В этом пошаговом руководстве предоставляет открытые свойства объекта, чтобы **свойства** окна. Изменения, внесенные в эти свойства, отражаются в **свойства** окна.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="exposing-properties-to-the-properties-window"></a>Предоставление доступа к свойствам в окне «Свойства»  
 В этом разделе Создание пользовательского окна инструментов и отобразить открытые свойства объекта области соответствующее окно в **свойства** окна.  
  
#### <a name="to-expose-properties-to-the-properties-window"></a>Экспорт свойств в окне «Свойства»  
  
1.  Все расширения Visual Studio начинается с проект развертывания VSIX, который будет содержать средств расширения. Создание [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проект VSIX с именем `MyObjectPropertiesExtension`. Шаблон проекта VSIX в можно найти **новый проект** диалогового окна в разделе **Visual C# / Extensibility**.  
  
2.  Добавить окно инструментов, добавив шаблон элемента пользовательского окна инструментов с именем `MyToolWindow`. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **добавить / новый элемент**. В **диалоговое окно добавления нового элемента**, перейдите в меню **элементы Visual C# / расширяемости** и выберите **окно инструментов настраиваемый**. В **имя** в нижней части диалогового окна, измените имя файла для `MyToolWindow.cs`. Дополнительные сведения о создании пользовательского окна инструментов см. в разделе [создания расширения с окном инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  Откройте MyToolWindow.cs и добавьте следующий код с помощью инструкции:  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4.  Теперь добавьте следующие поля, чтобы `MyToolWindow` класса.  
  
    ```csharp  
    private ITrackSelection trackSel;  
    private SelectionContainer selContainer;  
  
    ```  
  
5.  Добавьте следующий код в класс MyToolWindow.  
  
    ```csharp  
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
  
    public void UpdateSelection()  
    {  
        ITrackSelection track = TrackSelection;  
        if (track != null)  
            track.OnSelectChange((ISelectionContainer)selContainer);  
    }  
  
    public void SelectList(ArrayList list)  
    {  
        selContainer = new SelectionContainer(true, false);  
        selContainer.SelectableObjects = list;  
        selContainer.SelectedObjects = list;  
        UpdateSelection();  
    }  
  
    public override void OnToolWindowCreated()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
     `TrackSelection` Используется свойством `GetService` для получения `STrackSelection` службу, которая предоставляет <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> интерфейса. `OnToolWindowCreated` Обработчик событий и `SelectList` метод образуют список выбранных объектов, содержащий только средство окна области сам объект. `UpdateSelection` Указывает метод **свойства** окно для отображения открытых свойств объекта панели окна инструментов.  
  
6.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр Visual Studio.  
  
7.  Если **свойства** окно не отображается, откройте его, нажав клавишу F4.  
  
8.  Откройте **MyToolWindow** окна. Его можно найти в **представления и другие окна**.  
  
     Открывается окно и открытые свойства области окна в **свойства** окна.  
  
9. Изменение **заголовок** свойство в **свойства** окна **Мои свойства объекта**.  
  
     Заголовок окна MyToolWindow изменяется соответствующим образом.  
  
## <a name="exposing-tool-window-properties"></a>Предоставление доступа к свойствам окна инструментов  
 В этом разделе добавьте окна инструментов и предоставлять его свойства. Изменения, внесенные в свойства, отражаются в **свойства** окна.  
  
#### <a name="to-expose-tool-window-properties"></a>Для предоставления свойств окна инструментов  
  
1.  Откройте MyToolWindow.cs и добавьте в класс MyToolWindow открытый логическое свойство IsChecked.  
  
    ```csharp  
    [Category("My Properties")]  
    [Description("MyToolWindowControl properties")]  
    public bool IsChecked  
    {  
        get {  
            if (base.Content == null)  return false;  
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;   
        }  
        set {  
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;  
        }  
    }  
    ```  
  
     Это свойство получает свое состояние из флажок WPF, который будет создан в более поздней версии.  
  
2.  Откройте MyToolWindowControl.xaml.cs и замените конструктор MyToolWindowControl следующий код.  
  
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
  
3.  В MyToolWindow.cs, измените `MyToolWindow` конструктор следующим образом:  
  
    ```csharp  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4.  Изменить в представлении конструирования MyToolWindowControl.  
  
5.  Кнопка «Удалить» и добавьте флажок из **элементов** верхний левый угол.  
  
6.  Добавьте Checked и Unchecked события. Установите флажок в режиме конструктора. В **свойства** окно, нажмите кнопку обработчиков событий (в верхней правой части **свойства** окна). Найти **Checked** и тип **checkbox_Checked** в текстовом поле Найти **Unchecked** и тип **checkbox_Unchecked** в текстовом поле.  
  
7.  Добавьте обработчики событий флажок:  
  
    ```csharp  
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
  
     Найдите в окне свойств в **свойства** окна. **IsChecked** свойство появляется в нижней части окна, в разделе **свойства: Мой** категории.  
  
10. Установите флажок **MyToolWindow** окна. **IsChecked** в **свойства** примет вид окна **True**. Снимите флажок в **MyToolWindow** окна. **IsChecked** в **свойства** примет вид окна **False**. Измените значение **IsChecked** в **свойства** окна. Флажок в **MyToolWindow** окна изменяется в соответствии с новым значением.  
  
    > [!NOTE]
    >  Если необходимо уничтожить объект, который отображается в **свойства** окна, вызовите `OnSelectChange` с `null` контейнера выбора первого. После удаления свойство или объект, можно изменить для контейнера выделения, который был обновлен <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> и <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> перечислены.  
  
## <a name="changing-selection-lists"></a>Изменение списков выбора  
 В этом разделе добавления списка выбора для основных свойств класса и позволяет выбрать какой список выбора для отображения интерфейс окна средства.  
  
#### <a name="to-change-selection-lists"></a>Изменение списков выбора  
  
1.  Откройте MyToolWindow.cs и добавьте открытый класс с именем `Simple`.  
  
    ```csharp  
    public class Simple  
    {  
        private string someText = "";  
  
        [Category("My Properties")]  
        [Description("Simple Properties")]  
        [DisplayName("My Text")]  
        public string SomeText  
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
  
2.  Добавить свойство SimpleObject класса MyToolWindow, а также способов переключения **свойства** окна выбора между панели окна и `Simple` объекта.  
  
    ```csharp  
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
  
3.  В файл MyToolWindowControl.cs замените обработчики флажок следующие строки кода:  
  
    ```csharp  
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
  
6.  Установите флажок в **MyToolWindow** окна. **Свойства** отображает окно `Simple` свойства, объекта **SomeText** и **ReadOnly**. Снимите флажок. Открытые свойства окна отображаются в **свойства** окна.  
  
    > [!NOTE]
    >  Отображаемое имя **SomeText** — **мой текст**.  
  
## <a name="best-practice"></a>Рекомендации  
 В этом пошаговом руководстве <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> реализуется так, доступный для выбора объект коллекции и коллекции выбранных объектов и той же коллекции. В списке свойства браузера отображается только выбранный объект. Для более полной реализации ISelectionContainer см. в примерах Reference.toolwindow на языке.  
  
 Окна инструментов Visual Studio сохраняются между сеансами Visual Studio. Дополнительные сведения о сохранении состояние окна инструментов см. в разделе <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## <a name="see-also"></a>См. также  
 [Расширение свойств и окна свойств](../extensibility/extending-properties-and-the-property-window.md)