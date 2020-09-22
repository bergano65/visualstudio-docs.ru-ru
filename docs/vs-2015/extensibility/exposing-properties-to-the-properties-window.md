---
title: Предоставление свойств окну "Свойства" | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
caps.latest.revision: 37
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c28a0520680951920ee19e91f3df098066f432dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842464"
---
# <a name="exposing-properties-to-the-properties-window"></a>Предоставление свойств в окно свойств
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве общие свойства объекта представлены в окне **Свойства** . Изменения, вносимые в эти свойства, отражаются в окне **Свойства** .  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="exposing-properties-to-the-properties-window"></a>Предоставление свойств в окно свойств  
 В этом разделе вы создадите пользовательское окно инструментов и отобразите открытые свойства соответствующего объекта области окна в окне **Свойства** .  
  
#### <a name="to-expose-properties-to-the-properties-window"></a>Предоставление свойств окно свойств  
  
1. Каждое расширение Visual Studio начинается с проекта развертывания VSIX, который будет содержать ресурсы расширения. Создайте [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] проект VSIX с именем `MyObjectPropertiesExtension` . Шаблон проекта VSIX можно найти в диалоговом окне **Новый проект** в разделе **Visual C#/Extensibility (расширяемость**).  
  
2. Добавьте окно инструментов, добавив пользовательский шаблон элемента окна инструментов с именем `MyToolWindow` . В **Обозреватель решений**щелкните правой кнопкой мыши узел проекта и выберите **Добавить/новый элемент**. В **диалоговом окне Добавление нового элемента**перейдите к **элементу Visual C# элементы/Расширяемость** и выберите **настраиваемое окно инструментов**. В поле **имя** в нижней части диалогового окна измените имя файла на `MyToolWindow.cs` . Дополнительные сведения о создании настраиваемого окна инструментов см. в разделе [Создание расширения с помощью окна инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3. Откройте MyToolWindow.cs и добавьте следующую инструкцию using:  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4. Теперь добавьте в класс следующие поля `MyToolWindow` .  
  
    ```csharp  
    private ITrackSelection trackSel;  
    private SelectionContainer selContainer;  
  
    ```  
  
5. Добавьте следующий код в класс MyToolWindow.  
  
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
  
     `TrackSelection`Свойство использует `GetService` для получения `STrackSelection` службы, предоставляющей <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> интерфейс. `OnToolWindowCreated`Обработчик и метод события `SelectList` вместе создают список выбранных объектов, содержащих только сам объект области окна инструментов. `UpdateSelection`Метод сообщает окну **свойств** о необходимости отобразить открытые свойства панели окна инструментов.  
  
6. Выполните сборку решения и запустите отладку. Должен отобразиться экспериментальный экземпляр Visual Studio.  
  
7. Если окно **Свойства** не отображается, откройте его, нажав клавишу F4.  
  
8. Откройте окно **MyToolWindow** . Его можно найти в **представлении или других окнах**.  
  
     Откроется окно, и в окне « **Свойства** » отобразятся открытые свойства панели «окно».  
  
9. Измените свойство **Caption** в окне " **Свойства** " на " **мои свойства объекта**".  
  
     Заголовок окна MyToolWindow изменится соответствующим образом.  
  
## <a name="exposing-tool-window-properties"></a>Предоставление доступа к свойствам окна инструментов  
 В этом разделе вы добавите окно инструментов и предоставите его свойства. Изменения, вносимые в свойства, отражаются в окне **Свойства** .  
  
#### <a name="to-expose-tool-window-properties"></a>Предоставление свойств окна инструментов  
  
1. Откройте MyToolWindow.cs и добавьте открытое логическое свойство, возвращенное в класс MyToolWindow.  
  
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
  
     Это свойство получает свое состояние из флажка WPF, которое будет создано позже.  
  
2. Откройте MyToolWindowControl.xaml.cs и замените конструктор Митулвиндовконтрол следующим кодом.  
  
    ```vb  
    private MyToolWindow pane;  
    public MyToolWindowControl(MyToolWindow pane)  
    {  
        InitializeComponent();  
        this.pane = pane;  
        checkBox.IsChecked = false;  
    }  
    ```  
  
     Это дает `MyToolWindowControl` доступ к `MyToolWindow` панели.  
  
3. В MyToolWindow.cs измените `MyToolWindow` конструктор следующим образом:  
  
    ```csharp  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4. Перейдите в режим конструктора Митулвиндовконтрол.  
  
5. Удалите кнопку и добавьте флажок с **панели элементов** в левый верхний угол.  
  
6. Добавьте отмеченные и непроверенные события. Установите флажок в представлении конструктора. В окне **Свойства** нажмите кнопку обработчики событий (в правом верхнем углу окна **свойства** ). Найдите в текстовом поле **проверяемый** и тип **checkbox_Checked** , а затем найдите **непроверенные** и введите **checkbox_Unchecked** в текстовом поле.  
  
7. Добавьте обработчики событий с флажками:  
  
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
  
9. В экспериментальном экземпляре откройте окно **MyToolWindow** .  
  
     Найдите свойства окна в окне **Свойства** . Свойство «не **Проверено** » отображается в нижней части окна в категории « **мои свойства** ».  
  
10. Установите флажок в окне **MyToolWindow** . При **проверке** в окне " **Свойства** " изменяется на **true**. Снимите флажок в окне **MyToolWindow** . При **проверке** в окне " **Свойства** " изменяется на **false**. Измените значение параметра « **Проверка** » в окне « **свойства** ». Флажок в окне **MyToolWindow** изменится в соответствии с новым значением.  
  
    > [!NOTE]
    > Если необходимо удалить объект, который отображается в окне " **Свойства** ", сначала вызовите `OnSelectChange` с `null` контейнером выбора. После удаления свойства или объекта можно перейти к контейнеру выбора, который содержит обновленные <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> списки и.  
  
## <a name="changing-selection-lists"></a>Изменение списков выбора  
 В этом разделе вы добавите список выбора для базового класса свойств и с помощью интерфейса окна инструментов выберите отображаемый список выбора.  
  
#### <a name="to-change-selection-lists"></a>Изменение списков выбора  
  
1. Откройте MyToolWindow.cs и добавьте открытый класс с именем `Simple` .  
  
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
  
2. Добавьте свойство Симплеобжект в класс MyToolWindow и два метода, чтобы переключить выбор окна **свойств** между областью окна и `Simple` объектом.  
  
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
  
3. В MyToolWindowControl.cs замените обработчики флажков следующими строками кода:  
  
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
  
5. В экспериментальном экземпляре откройте окно **MyToolWindow** .  
  
6. Установите флажок в окне **MyToolWindow** . В окне **Свойства** отображаются `Simple` свойства объекта **сометекст** и **ReadOnly**. Снимите флажок. Открытые свойства окна отображаются в окне **Свойства** .  
  
    > [!NOTE]
    > Отображаемое имя **сометекст** — **мой текст**.  
  
## <a name="best-practice"></a>Рекомендации  
 В этом пошаговом руководстве <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> реализуется, чтобы коллекция выбираемых объектов и выбранная коллекция объектов были одной и той же коллекцией. В списке браузер свойств появится только выбранный объект. Более полную реализацию Иселектионконтаинер см. в разделе примеры Reference. reинструментов.  
  
 Окна инструментов Visual Studio сохраняются между сеансами Visual Studio. Дополнительные сведения о сохранении состояния окна инструментов см. в разделе <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> .  
  
## <a name="see-also"></a>См. также:  
 [Расширение свойств и окна свойств](../extensibility/extending-properties-and-the-property-window.md)
