---
title: Предоставление доступа к свойствам, окно "Свойства" | Документация Майкрософт
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2cd1f44342199c26506cceb4c77378b13aefd566
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341228"
---
# <a name="expose-properties-to-the-properties-window"></a>Свойств в окне «Свойства»

В этом пошаговом руководстве предоставляет открытые свойства объекта, чтобы **свойства** окна. Изменения, внесенные в эти свойства, отражаются в **свойства** окна.

## <a name="prerequisites"></a>Предварительные требования

Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установить пакет SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="expose-properties-to-the-properties-window"></a>Свойств в окне «Свойства»

В этом разделе описано, создание пользовательского окна инструментов и отобразить открытые свойства объекта области окна в **свойства** окна.

### <a name="to-expose-properties-to-the-properties-window"></a>Экспорт свойств в окне «Свойства»

1. Все расширения Visual Studio начинается с развертывания проект VSIX, который будет содержать средств расширения. Создание [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проект VSIX с именем `MyObjectPropertiesExtension`. Вы найдете шаблон проекта VSIX в **новый проект** диалоговое окно, выполняя поиск «vsix».

2. Добавление окна инструментов, добавив шаблон элемента пользовательского окна инструментов с именем `MyToolWindow`. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **добавить** > **новый элемент**. В **диалоговое окно Add New Item**, перейдите в меню **элементы Visual C#**  > **расширяемости** и выберите **окно инструментов Custom**. В **имя** в нижней части диалогового окна, измените имя файла для *MyToolWindow.cs*. Дополнительные сведения о создании пользовательского окна инструментов см. в разделе [создание расширения с окном инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Откройте *MyToolWindow.cs* и добавьте следующий оператор using:

   ```csharp
   using System.Collections;
   using System.ComponentModel;
   using Microsoft.VisualStudio.Shell.Interop;
   ```

4. Теперь добавьте следующие поля в `MyToolWindow` класса.

   ```csharp
   private ITrackSelection trackSel;
   private SelectionContainer selContainer;

   ```

5. Добавьте следующий код в класс `MyToolWindow` .

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

    `TrackSelection` Используется в свойстве `GetService` для получения `STrackSelection` службу, которая обеспечивает <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> интерфейс. `OnToolWindowCreated` Обработчик событий и `SelectList` метод вместе создаст список выбранных объектов, содержащий только средство окно области самого объекта. `UpdateSelection` Метод указывает **свойства** окно для отображения открытых свойств панели окна инструментов.

6. Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр Visual Studio.

7. Если **свойства** окно не отображается, откройте его, нажав клавишу **F4**.

8. Откройте **MyToolWindow** окна. Его можно найти в **представление** > **Other Windows**.

    Открывается окно и общедоступного свойства области окна в **свойства** окна.

9. Изменение **заголовок** свойство в **свойства** окно, чтобы **свойства: Мой объект**.

     Заголовок окна MyToolWindow изменяется соответствующим образом.

## <a name="expose-tool-window-properties"></a>Предоставляют свойства окна инструментов

В этом разделе описано как добавить окно инструмента и предоставляют его свойства. Изменения, внесенные в свойства, отражаются в **свойства** окна.

### <a name="to-expose-tool-window-properties"></a>Для предоставления свойства окна инструментов

1. Откройте *MyToolWindow.cs*, и добавьте открытый логическое свойство IsChecked для `MyToolWindow` класса.

    ```csharp
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

     Это свойство получает свое состояние из WPF флажок, который будет создан позже.

2. Откройте *MyToolWindowControl.xaml.cs* и замените следующий код в конструктор MyToolWindowControl.

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

3. В *MyToolWindow.cs*, изменить `MyToolWindow` конструктор следующим образом:

    ```csharp
    base.Content = new MyToolWindowControl(this);
    ```

4. Изменить в режиме конструктора MyToolWindowControl.

5. Кнопка "Удалить" и добавьте типа "флажок" из **элементов** верхний левый угол.

6. Добавьте Checked и Unchecked события. Установите флажок в режиме конструктора. В **свойства** окно, нажмите кнопку обработчики событий (в верхней правой части **свойства** окна). Найти **Checked** и тип **checkbox_Checked** в текстовом поле, затем найдите **Unchecked** и тип **checkbox_Unchecked** в текстовом поле.

7. Добавление обработчиков событий флажок:

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

8. Выполните сборку решения и запустите отладку.

9. В экспериментальном экземпляре откройте **MyToolWindow** окна.

     Поиск окна свойств в **свойства** окна. **IsChecked** свойство отображается в нижней части окна, в разделе **свойства: Мой** категории.

10. Установите флажок **MyToolWindow** окна. **IsChecked** в **свойства** окна изменяется на **True**. Снимите флажок в **MyToolWindow** окна. **IsChecked** в **свойства** окна изменяется на **False**. Измените значение свойства **IsChecked** в **свойства** окна. Флажок в **MyToolWindow** окна меняется в соответствии с новым значением.

    > [!NOTE]
    > Если необходимо уничтожить объект, который отображается в **свойства** окна, вызовите `OnSelectChange` с `null` контейнер выделения первой. После удаления, свойство или объект, можно изменить для контейнера выделения, который был обновлен <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> и <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> перечислены.

## <a name="change-selection-lists"></a>Изменить списки выбора

 В этом разделе добавьте список выбора для основных свойств класса и используйте интерфейс окна инструментов, чтобы выбрать список выбора для отображения.

### <a name="to-change-selection-lists"></a>Чтобы изменить списки выбора

1. Откройте *MyToolWindow.cs* и добавьте открытый класс с именем `Simple`.

    ```csharp
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

2. Добавить `SimpleObject` свойства `MyToolWindow` класс, а также два метода для переключения **свойства** выбора окна между область окна и `Simple` объекта.

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

3. В *файл MyToolWindowControl.cs*, замените обработчики флажок эти строки кода:

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

4. Выполните сборку решения и запустите отладку.

5. В экспериментальном экземпляре откройте **MyToolWindow** окна.

6. Установите флажок в **MyToolWindow** окна. **Свойства** окно отображает `Simple` объект свойства, **SomeText** и **ReadOnly**. Снимите флажок. Открытые свойства окна отображаются в **свойства** окна.

    > [!NOTE]
    > Отображаемое имя **SomeText** — **текст моего**.

## <a name="best-practice"></a>Рекомендации

В этом пошаговом руководстве <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> реализуется так, доступный для выбора объект коллекции и коллекции выбранного объекта и той же коллекции. Только выбранный объект отображается в списке обозревателя свойств. Более полная реализация ISelectionContainer см. в примерах Reference.toolwindow на языке.

Окна инструментов Visual Studio сохраняются между сеансами Visual Studio. Дополнительные сведения о сохранении состояние окна инструментов, см. в разделе <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.

## <a name="see-also"></a>См. также

- [Расширение свойств и окна свойств](../extensibility/extending-properties-and-the-property-window.md)