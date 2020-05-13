---
title: Разоблачение Свойства к оклеить свойства (ru) Документы Майкрософт
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f84962628ae550676e2c2eeb10c0f3baeca1bb58
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711832"
---
# <a name="expose-properties-to-the-properties-window"></a>Выставляет свойства в окно Свойств

Это пошаговое окно предоставляет публичные свойства объекта окну **Свойства.** Изменения, внесенные в эти свойства, отражаются в окне **свойств.**

## <a name="prerequisites"></a>Предварительные требования

Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="expose-properties-to-the-properties-window"></a>Выставляет свойства в окно Свойств

В этом разделе необходимо создать пользовательское окно инструмента и отобразить общедоступные свойства связанного объекта оконного стекла в окне **Свойств.**

### <a name="to-expose-properties-to-the-properties-window"></a>Для размещения свойств в окне свойств

1. Каждое расширение Visual Studio начинается с проекта развертывания VSIX, который будет содержать активы расширения. Создайте [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проект VSIX под названием `MyObjectPropertiesExtension`. Шаблон проекта VSIX можно найти в диалоге **нового проекта,** ища "vsix".

2. Добавьте окно инструмента, добавив шаблон элемента Custom Tool Window под названием. `MyToolWindow` В **Solution Explorer**, правой кнопкой мыши узла проекта и выберите **Добавить** > **новый пункт**. В **диалоге Добавить новый элемент**, перейдите к **Visual C' Элементы** > **Расширяемость** и выберите **пользовательский инструмент окно**. В поле **«Имя»** в нижней части диалога измените имя файла на *MyToolWindow.cs.* Для получения дополнительной информации о том, как создать пользовательское окно инструмента, [см.](../extensibility/creating-an-extension-with-a-tool-window.md)

3. Откройте *MyToolWindow.cs* и добавьте следующее с помощью оператора:

   ```csharp
   using System.Collections;
   using System.ComponentModel;
   using Microsoft.VisualStudio.Shell.Interop;
   ```

4. Теперь добавьте следующие поля в `MyToolWindow` класс.

   ```csharp
   private ITrackSelection trackSel;
   private SelectionContainer selContainer;

   ```

5. Добавьте в класс `MyToolWindow` приведенный далее код.

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

    Свойство `TrackSelection` `GetService` использует для `STrackSelection` получения услуги, которая обеспечивает <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> интерфейс. Обработчик `OnToolWindowCreated` `SelectList` событий и метод вместе создают список выбранных объектов, который содержит только сам объект панели окна инструмента. Метод `UpdateSelection` сообщает окну **Свойств** для отображения общедоступных свойств оконного стекла инструмента.

6. Выполните сборку решения и запустите отладку. Экспериментальный экземпляр Visual Studio должен появиться.

7. Если окно **Properties** не видно, откройте его нажатием **F4.**

8. Откройте окно **MyToolWindow.** Вы можете найти его в **просмотре** > **другие Windows**.

    Окно открывается, и в окне **Свойства** отображаются общественные свойства оконного стекла.

9. Измените свойство **caption** в окне **свойств** на **my Object Properties.**

     Подпись окна MyToolWindow изменяется соответствующим образом.

## <a name="expose-tool-window-properties"></a>Экспонировать свойства окна инструмента

В этом разделе вы добавляете окно инструмента и раскрываете его свойства. Изменения, внесенные в свойства, отражаются в окне **свойств.**

### <a name="to-expose-tool-window-properties"></a>Для выявления свойств окна инструмента

1. Откройте *MyToolWindow.cs,* и добавить общественные boolean собственности IsChecked в `MyToolWindow` класс.

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

     Это свойство получает свое состояние из флажка WPF, который вы создадите позже.

2. Откройте *MyToolWindowControl.xaml.cs* и замените конструктор MyToolWindowControl следующим кодом.

    ```vb
    private MyToolWindow pane;
    public MyToolWindowControl(MyToolWindow pane)
    {
        InitializeComponent();
        this.pane = pane;
        checkBox.IsChecked = false;
    }
    ```

     Это `MyToolWindowControl` дает доступ `MyToolWindow` к стеку.

3. В *MyToolWindow.cs,* `MyToolWindow` изменить конструктор следующим образом:

    ```csharp
    base.Content = new MyToolWindowControl(this);
    ```

4. Изменение представления дизайна MyToolWindowControl.

5. Удалите кнопку и добавьте флажок из **ящика для инструментов** в левый верхний угол.

6. Добавьте Проверенные и неконтролируемые события. Выберите флажок в представлении дизайна. В окне **Свойств** нажмите кнопку обработчиков событий (в правом верхнем правом верхнем правом окне **свойства).** Найти **Проверенные** и введите **checkbox_Checked** в текстовом поле, а затем найти **Unchecked** и введите **checkbox_Unchecked** в текстовом поле.

7. Добавьте обработчики событий флажка:

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

9. В экспериментальном примере откройте окно **MyToolWindow.**

     Ищите свойства окна в окне **Свойства.** Свойство **IsChecked** отображается в нижней части окна в категории **My Properties.**

10. Проверьте флажок в окне **MyToolWindow.** **Проверено** в окне **Свойства** изменения на **True**. Очистите флажок в окне **MyToolWindow.** **Проверено** в окне **Свойства** изменения на **ложные**. Измените значение **IsChecked** в окне **свойств.** Флажок в окне **MyToolWindow** изменяется в соответствии с новым значением.

    > [!NOTE]
    > Если необходимо избавиться от объекта, отображаемого `null` в окне **Свойств,** сначала позвоните `OnSelectChange` в контейнер выбора. После удаления свойства или объекта можно изменить на <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> обновляемый <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> и список контейнера выбора.

## <a name="change-selection-lists"></a>Изменить списки выбора

 В этом разделе вы добавляете список выбора для базового класса свойств и используете интерфейс окна инструмента, чтобы выбрать, какой список выбора для отображения.

### <a name="to-change-selection-lists"></a>Изменение списков выбора

1. Откройте *MyToolWindow.cs* и добавьте общедоступный класс с именем `Simple`.

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

2. Добавьте `SimpleObject` свойство `MyToolWindow` в класс, а также два метода для переключения выбора окна **Свойств** между оконным стеклом и объектом. `Simple`

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

3. В *MyToolWindowControl.cs*замените обработчики флажков на эти строки кода:

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

5. В экспериментальном примере откройте окно **MyToolWindow.**

6. Выберите флажок в окне **MyToolWindow.** Окно **Свойства** отображает `Simple` свойства объекта, **SomeText** и **ReadOnly**. Очистите флажок. Публичные свойства окна отображаются в окне **Свойств.**

    > [!NOTE]
    > Название отображения **SomeText** мой **текст**.

## <a name="best-practice"></a>Рекомендации

В этом пошаговом шаге <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> реализована такая же коллекция, как выбрать объект, и выбранная коллекция объектов. В списке браузера свойств отображается только выбранный объект. Для более полной реализации I-SelectionContainer см.

Окна инструментов Visual Studio сохраняются между сеансами Visual Studio. Для получения дополнительной информации о сохранении состояния окна инструмента см. <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>

## <a name="see-also"></a>См. также

- [Расширить свойства и окно свойства](../extensibility/extending-properties-and-the-property-window.md)
