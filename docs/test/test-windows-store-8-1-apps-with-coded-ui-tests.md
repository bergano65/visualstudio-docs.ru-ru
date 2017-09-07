---
title: "Тестирование приложений Windows UWP и приложений Магазина Windows 8.1 с помощью закодированных тестов пользовательского интерфейса | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8d9c15e-ce3c-401a-86ec-c5c124a239d8
caps.latest.revision: 23
ms.author: douge
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 2a9dc338ce3d08ac61ecc77da8df96d9261b7e62
ms.contentlocale: ru-ru
ms.lasthandoff: 09/06/2017

---
# <a name="test-windows-uwp-and-81-store-apps-with-coded-ui-tests"></a>Тестирование приложений Windows UWP и приложений Магазина Windows 8.1 с помощью закодированных тестов пользовательского интерфейса

В этом пошаговом руководстве описывается создание тестов пользовательского интерфейса для приложений UWP и приложений на основе XAML Магазина Windows 8.1. 
  
## <a name="create-a-simple-windows-store-app"></a>Создание простого приложения Магазина Windows  
  
1.  Чтобы выполнять закодированные тесты ИП для XAML-приложения Магазина Windows, необходимо [настроить уникальное свойство автоматизации, определяющее каждый элемент управления](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md).  
  
     В меню **Сервис** выберите пункт **Параметры** и щелкните **Текстовый редактор**, выберите **XAML**и **Прочее**.  
  
     Установите флажок, чтобы автоматически именовать интерактивные элементы при создании.  
  
     ![Прочие параметры XAML](../test/media/cuit_windowsstoreapp_b.png "CUIT_WindowsStoreApp_B")  
  
2.  Создайте проект пустого XAML-приложения Магазина Windows, используя шаблон Visual C# или Visual Basic.  
  
     ![Создание пустого приложения для Магазина Windows &#40;XAML&#41;](../test/media/cuit_windowsstoreapp_newproject_blankstoreapp.png "CUIT_WindowsStoreApp_NewProject_BlankStoreApp")  
  
3.  В обозревателе решений выберите файл MainPage.xaml. Из панели инструментов перетащите элемент управления "Кнопка" и "Текстовое поле" на поверхность разработки.  
  
     ![Проектирование приложения для Магазина Windows](../test/media/cuit_windowsstoreapp_design.png "CUIT_WindowsStoreApp_Design")  
  
4.  Дважды щелкните элемент управления "Кнопка" и добавьте следующий код:  
  
    ```csharp  
    private void button_Click_1(object sender, RoutedEventArgs e)  
    {  
        this.textBox.Text = this.button.Name;  
    }  
  
    ```  
  
    ```vb  
    Public NotInheritable Class MainPage  
        Inherits Page  
  
        Private Sub button_Click(sender As Object, e As RoutedEventArgs) Handles Button.Click  
            Me.textBox.Text = Me.button.Name  
        End Sub  
    End Class  
    ```  
  
5.  Нажмите клавишу F5, чтобы запустить приложение Магазина Windows.  
  
## <a name="create-and-run-a-coded-ui-test-for-the-windows-store-app"></a>Создание и запуск закодированного теста ИП для приложения Магазина Windows  

[Как создать закодированные тесты пользовательского интерфейса для приложений универсальной платформы Windows (UWP)?](#uwpapps)
  
1.  Создайте проект закодированного теста ИП для приложения Магазина Windows.  
  
     ![Новый проект закодированного теста пользовательского интерфейса &#40;приложения для Магазина Windows&#41;](../test/media/cuit_windowsstore_newproject.png "CUIT_WindowsStore_NewProject")  
  
2.  С помощью перекрестия включите режим редактирования карты ИП.  
  
     ![Выбор изменения карты пользовательского интерфейса или добавления утверждений](../test/media/cuit_windowsstoreapp_createproject_gencodedialog.png "CUIT_WindowsStoreApp_CreateProject_GenCodeDialog")  
  
3.  Выберите плитку приложения с помощью перекрестья в построителе закодированных тестов ИП, щелкните правой кнопкой свойство **AutomationId** и выберите команду **Скопировать значение в буфер обмена**. Это значение будет использоваться позднее для записи действия, необходимого для запуска тестируемого приложения.  
  
     ![Копирование AutomationId в буфер обмена](../test/media/cuit_windows_store_tileautomationid.png "CUIT_Windows_Store_TileAutomationID")  
  
4.  В запущенном приложении Магазина Windows с помощью перекрестья выберите элемент управления "Кнопка" и "Текстовое поле". После добавления каждого элемента управления нажмите кнопку **Добавить элемент управления на карту элементов управления ИП** на панели инструментов построителя закодированных тестов ИП.  
  
     ![Добавление элемента на карту пользовательского интерфейса](../test/media/cuit_windowsstoreapp_uimap.png "CUIT_WindowsStoreApp_UIMap")  
  
5.  Нажмите кнопку **Создать код** на панели инструментов построителя закодированных тестов ИП и щелкните **Создать** , чтобы сформировать код изменений карты элементов управления ИП.  
  
     ![Формирование кода для карты пользовательского интерфейса](../test/media/cuit_windowsstoreapp_generate.png "CUIT_WindowsStoreApp_Generate")  
  
6.  Выберите кнопку, чтобы задать значение в текстовом поле.  
  
     ![Нажмите элемент управления "кнопка", чтобы задать значение текстового поля](../test/media/cuit_windowsstoreapp_clickbutton.png "CUIT_WindowsStoreApp_ClickButton")  
  
7.  С помощью перекрестья выберите текстовое поле, а затем свойство **Text** .  
  
     ![Выбор свойства Text](../test/media/cuit_windowsstoreapp_selecttextproperty.png "CUIT_WindowsStoreApp_SelectTextProperty")  
  
8.  Добавьте утверждение. Оно будет использоваться для проверки значения.  
  
     ![Выбор текстового поля с помощью перекрестья и добавление утверждения](../test/media/cuit_windowsstoreapp_textbox_addassertion.png "CUIT_WindowsStoreApp_Textbox_AddAssertion")  
  
9. Добавьте и создайте код для утверждения.  
  
     ![Формирование кода для утверждения текстового поля](../test/media/cuit_windowsstoreapp_textbox_generate_assertion.png "CUIT_WindowsStoreApp_Textbox_Generate_Assertion")  
  
10. **Visual C#**  
  
     В обозревателе решений откройте файл UIMap.Designer.cs, чтобы просмотреть добавленный код для метода assert и элементов управления.  
  
     **Visual Basic**  
  
     В обозревателе решений откройте файл CodedUITest1.vb и затем в коде метода теста CodedUITestMethod1() щелкните правой кнопкой вызов метода assert, который был автоматически добавлен в `Me.UIMap.AssertMethod1()` , и выберите команду **Перейти к определению**. Файл UIMap.Designer.vb откроется в редакторе кода, где вы сможете просмотреть код, добавленный для метода assert и элементов управления.  
  
    > [!WARNING]
    >  Не изменяйте файл UIMap.Designer.cs или UIMap.Designer.vb напрямую. В этом случае изменения файла будут перезаписываться при каждом создании теста.  
  
     **Метод Assert**  
  
    ```csharp  
    public void AssertMethod1()  
    {  
        #region Variable Declarations  
        XamlEdit uITextBoxEdit = this.UIApp1Window.UITextBoxEdit;  
        #endregion  
  
        // Verify that the 'Text' property of 'textBox' text box equals 'button'  
        Assert.AreEqual(this.AssertMethod3ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text);  
    }  
    ```  
  
    ```vb  
    Public Sub AssertMethod1()  
        Dim uITextBoxEdit As XamlEdit = Me.UIApp2Window.UITextBoxEdit  
  
        'Verify that the 'Text' property of 'textBox' text box equals 'button'  
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text)  
    End Sub  
    ```  
  
     **Элементы управления**  
  
    ```csharp  
    #region Properties  
    public XamlButton UIButtonButton  
    {  
        get  
        {  
            if ((this.mUIButtonButton == null))  
            {  
                this.mUIButtonButton = new XamlButton(this);  
                #region Search Criteria  
                this.mUIButtonButton.SearchProperties[XamlButton.PropertyNames.AutomationId] = "button";  
                this.mUIButtonButton.WindowTitles.Add("App1");  
                #endregion  
            }  
            return this.mUIButtonButton;  
        }  
    }  
  
    public XamlEdit UITextBoxEdit  
    {  
        get  
        {  
            if ((this.mUITextBoxEdit == null))  
            {  
                this.mUITextBoxEdit = new XamlEdit(this);  
                #region Search Criteria  
                this.mUITextBoxEdit.SearchProperties[XamlEdit.PropertyNames.AutomationId] = "textBox";  
                this.mUITextBoxEdit.WindowTitles.Add("App1");  
                #endregion  
            }  
            return this.mUITextBoxEdit;  
        }  
    }  
    #endregion  
  
    #region Fields  
    private XamlButton mUIButtonButton;  
  
    private XamlEdit mUITextBoxEdit;  
    #endregion  
    ```  
  
    ```vb  
    #Region "Properties"  
    Public ReadOnly Property UIButtonButton() As XamlButton  
        Get  
            If (Me.mUIButtonButton Is Nothing) Then  
                Me.mUIButtonButton = New XamlButton(Me)  
                Me.mUIButtonButton.SearchProperties(XamlButton.PropertyNames.AutomationId) = "button"  
                Me.mUIButtonButton.WindowTitles.Add("App2")  
            End If  
            Return Me.mUIButtonButton  
        End Get  
    End Property  
  
    Public ReadOnly Property UITextBoxEdit() As XamlEdit  
        Get  
            If (Me.mUITextBoxEdit Is Nothing) Then  
                Me.mUITextBoxEdit = New XamlEdit(Me)  
                Me.mUITextBoxEdit.SearchProperties(XamlEdit.PropertyNames.AutomationId) = "textBox"  
                Me.mUITextBoxEdit.WindowTitles.Add("App2")  
            End If  
            Return Me.mUITextBoxEdit  
        End Get  
    End Property  
    #End Region  
  
    #Region "Fields"  
    Private mUIButtonButton As XamlButton  
  
    Private mUITextBoxEdit As XamlEdit  
    #End Region  
    ```  
  
11. В обозревателе решений откройте файл CodedUITest1.cs или CodedUITest1.vb. Теперь вы можете добавить код в метод CodedUTTestMethod1 для действий, необходимых для выполнения теста с использованием элементов управления, добавленных в UIMap:  
  
    1.  Запустите приложение Магазина Windows, используя свойство AutomationID, скопированное ранее в буфер обмена:  
  
        ```csharp  
        XamlWindow.Launch("8ebca7c4-effe-4c86-9998-068daccee452_cyrqexqw8cc7c!App")  
        ```  
  
        ```vb  
        XamlWindow myAppWindow = XamlWindow.Launch("7254db3e-20a7-424e-8e05-7c4dabf4f28d_cyrqexqw8cc7c!App");  
        ```  
  
    2.  Добавьте жест касания кнопки:  
  
        ```csharp  
        Gesture.Tap(this.UIMap.UIApp1Window. UIButtonButton);  
        ```  
  
        ```vb  
        Gesture.Tap(Me.UIMap.UIApp2Window. UIButtonButton)  
        ```  
  
    3.  Убедитесь, что вызов метода assert, созданного автоматически, следует после запуска приложения и касания кнопки:  
  
        ```csharp  
        this.UIMap.AssertMethod1();  
        ```  
  
        ```vb  
        Me.UIMap.AssertMethod1()  
        ```  
  
     После добавления кода метод теста CodedUITestMethod1 должен выглядеть следующим образом:  
  
    ```csharp  
    [TestMethod]  
    public void CodedUITestMethod1()  
    {  
        // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
  
        // Launch the app.  
        XamlWindow myAppWindow = XamlWindow.Launch("7254db3e-20a7-424e-8e05-7c4dabf4f28d_cyrqexqw8cc7c!App");  
  
        // Tap the button.  
        Gesture.Tap(this.UIMap.UIApp1Window.UIButtonButton);  
  
        this.UIMap.AssertMethod1();  
    }  
    ```  
  
    ```vb  
    <CodedUITest(CodedUITestType.WindowsStore)>  
    Public Class CodedUITest1  
  
        <TestMethod()>  
        Public Sub CodedUITestMethod1()  
            '              
            ' To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
            '  
  
            ' Launch the app.  
            XamlWindow.Launch("8ebca7c4-effe-4c86-9998-068daccee452_cyrqexqw8cc7c!App")  
  
            '// Tap the button.  
            Gesture.Tap(Me.UIMap.UIApp2Window.UIButtonButton)  
  
            Me.UIMap.AssertMethod1()  
        End Sub  
    ```  
  
12. Выполните построение теста и запустите его в обозревателе тестов.  
  
     ![Запуск закодированного теста пользовательского интерфейса из обозревателя тестов](../test/media/cuit_windowsstoreapp_runtest.png "CUIT_WindowsStoreApp_RunTest")  
  
     Приложение Магазина Windows запустится, будет выполнено действие касания кнопки, а свойство Text текстового поля будет заполнено и проверено с помощью метода assert.  
  
     ![Выполнение закодированного теста пользовательского интерфейса](../test/media/cuit_windowsstoreapp_running.png "CUIT_WindowsStoreApp_Running")  
  
     После завершения теста обозреватель тестов подтвердит, что тест был пройден.  
  
     ![Пройденный тест отображается в обозревателе тестов](../test/media/cuit_windowsstorapp_passedtest.png "CUIT_WindowsStorApp_PassedTest")  
  
## <a name="q--a"></a>Вопросы и ответы  
  
#### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>В. Почему я не вижу параметр для записи закодированного теста ИП в диалоговом окне "Создать код" или "Закодированный тест пользовательского интерфейса"? **  
  
**О**. Параметр записи не поддерживается для приложений Магазина Windows.  
  
#### <a name="q-can-i-create-a-coded-ui-test-for-my-windows-store-apps-based-on-winjs"></a>Вопрос. Можно ли создать закодированный тест пользовательского интерфейса для приложений Магазина Windows, написанных на WinJS?**  

**О**. Поддерживаются только приложения на XAML.  
  
#### <a name="q-can-i-create-coded-ui-tests-for-my-windows-store-apps-on-a-system-that-is-not-running-windows-81-or-windows-10"></a>Вопрос. Можно ли создать закодированные тесты пользовательского интерфейса для приложений Магазина Windows в системе, не работающей под управлением Windows 8.1 или Windows 10?**  
  
**О**. Нет. Шаблоны проекта закодированного теста пользовательского интерфейса доступны только для Windows 8.1 и Windows 10. Чтобы создать автоматизацию для приложений универсальной платформы Windows (UWP), потребуется Windows 10.  

<a name="uwpapps"></a>  
#### <a name="q-how-do-i-create-coded-ui-tests-for-universal-windows-platform-uwp-apps"></a>Вопрос. Как создать закодированные тесты пользовательского интерфейса для приложений универсальной платформы Windows (UWP)?**  
  
**О**. В зависимости от платформы, на которой выполняется тестирование приложения UWP, создание проекта закодированного теста ИП осуществляется одним из следующих способов.  
  
- Приложение UWP, работающее на локальном компьютере, будет выполняться как приложение для Магазина. Чтобы проверить это, необходимо использовать шаблон **проекта закодированного теста ИП (Windows)** . Чтобы найти этот шаблон при создании нового проекта, перейдите к узлу **Windows**, **Универсальный** . Или перейдите к узлу **Windows**, **Windows 8**, **Windows** .  
  
- Приложение UWP, работающее на мобильном устройстве или в эмуляторе, будет выполняться как приложение Windows Phone. Чтобы проверить это, необходимо использовать шаблон **проекта закодированного теста ИП (Windows Phone)** . Чтобы найти этот шаблон при создании нового проекта, перейдите к узлу **Windows**, **Универсальный** . Или перейдите к узлу **Windows**, **Windows 8**, **Windows Phone** .  
  
После создания проекта разработка теста остается прежней.  
  
#### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>В. Почему не следует изменять файл UIMap.Designer? **  
  
**О**. Любые изменения кода, внесенные в файл UIMapDesigner.cs, будут перезаписываться каждый раз при создании кода с помощью построителя кодированных тестов ИП. Если требуется изменить записанный метод, необходимо скопировать его в файл UIMap.cs и переименовать. Файл UIMap.cs можно использовать для переопределения методов и свойств в файле UIMapDesigner.cs. Необходимо удалить ссылку на исходный метод в файле CodedUITest.cs и заменить ее именем переименованного метода.  
  
## <a name="see-also"></a>См. также  
 [Использование модели автоматизации пользовательского интерфейса для тестирования кода](../test/use-ui-automation-to-test-your-code.md)   
 [Задание уникального свойства автоматизации элементов управления для Магазина Windows при тестировании](../test/set-a-unique-automation-property-for-windows-store-controls-for-testing.md)

