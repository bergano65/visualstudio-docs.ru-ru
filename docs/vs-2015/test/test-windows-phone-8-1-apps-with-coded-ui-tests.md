---
title: Тестирование приложений Windows UWP и приложений Windows Phone 8.1 с помощью закодированных тестов пользовательского интерфейса | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b866776-f2d5-4823-8d15-919f889db26f
caps.latest.revision: 31
ms.author: gewarren
manager: douge
ms.openlocfilehash: 604ac82fbcda190c63a15e5ba0a1800022853b07
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49285939"
---
# <a name="test-windows-uwp-and-81-phone-apps-with-coded-ui-tests"></a>Тестирование приложений Windows UWP и приложений Windows Phone 8.1 с помощью закодированных тестов пользовательского интерфейса
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве описывается создание тестов пользовательского интерфейса для приложений UWP, которые будут выполняться на мобильных устройствах или эмуляторах, а также в приложениях Windows Phone 8.1 на основе XAML.   
  
## <a name="create-a-simple-windows-phone-app"></a>Создание простого приложения Windows Phone  
  
1.  Создайте проект пустого приложения Windows Phone, используя шаблон Visual C# или Visual Basic.  
  
     ![Создание нового приложения Windows Phone](../test/media/cuit-phone-app-newproject.png "CUIT_Phone_App_NewProject")  
  
2.  В обозревателе решений выберите файл MainPage.xaml. Из панели инструментов перетащите элемент управления "Кнопка" и "Текстовое поле" на поверхность разработки.  
  
     ![Добавление элементов управления в MainPage.xaml](../test/media/cuit-phone-app-addcontrols.png "CUIT_Phone_App_AddControls")  
  
3.  В окне "Свойства" укажите имя кнопки  
  
     ![Присвоение имени элементу управления "кнопка"](../test/media/cuit-phone-namebutton.png "CUIT_Phone_NameButton")  
  
4.  и текстового поля.  
  
     ![Присвоение имени элементу управления текстового поля](../test/media/cuit-phone-nametesxtbox.png "CUIT_Phone_NameTesxtBox")  
  
5.  На поверхности разработки дважды щелкните элемент управления "Кнопка" и добавьте следующий код:  
  
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
  
6.  Нажмите клавишу F5, чтобы запустить приложение Windows Phone в эмуляторе и проверить его работу.  
  
     ![Запуск приложения Windows Phone](../test/media/cuit-phone-runapp.png "CUIt_Phone_RunApp")  
  
7.  Закройте эмулятор.  
  
## <a name="deploy-the-windows-phone-app"></a>Развертывание приложения Windows Phone  
  
1.  Чтобы закодированный тест ИП могут сопоставить элементы управления приложения, необходимо развернуть приложение.  
  
     ![Развертывание приложения Windows Phone](../test/media/cuit-phone-deploy.png "CUIT_Phone_Deploy")  
  
     Запускается эмулятор. Теперь приложение можно протестировать.  
  
     ![Приложение, развернутое в эмуляторе](../test/media/cuit-phone-deployed.png "CUIT_Phone_Deployed")  
  
     Не закрывайте эмулятор при создании закодированного теста ИП.  
  
## <a name="create-a-coded-ui-test-for-the-windows-phone-app"></a>Создание закодированного теста ИП для приложения Windows Phone  

[Как создать закодированные тесты пользовательского интерфейса для приложений универсальной платформы Windows (UWP)?](#uwpapps)
  
1.  Добавьте новый проект закодированного теста ИП в решение с приложением Windows Phone.  
  
     ![Создание закодированного теста пользовательского интерфейса для Windows Phone](../test/media/cuit-phone-newproject.png "CUIT_Phone_NewProject")  
  
2.  С помощью перекрестия включите режим редактирования карты ИП.  
  
     ![Создание закодированного теста пользовательского интерфейса с помощью перекрестья](../test/media/cuit-phone-howgencodedialog.png "CUIT_Phone_HowGenCodeDialog")  
  
3.  Выберите приложение, а затем скопируйте значение свойства **AutomationId** , которое будет использоваться для запуска приложения в тесте.  
  
     ![Копирование значения AutomationId приложения](../test/media/cuit-phone-getautomationid.png "CUIT_Phone_GetAutomationId")  
  
4.  Запустите приложение в эмуляторе и с помощью перекрестья выберите элемент управления "Кнопка". Затем добавьте элемент управления на карту ИП.  
  
     ![Использование перекрестья для сопоставления элементов управления](../test/media/cuit-phone-mapbuttoncontrol.png "CUIT_Phone_MapButtonControl")  
  
5.  Повторите этот шаг, чтобы добавить элемент управления "Текстовое поле" на карту ИП.  
  
     ![Использование перекрестья для сопоставления элемента управления типа "текстовое поле"](../test/media/cuit-phone-maptextboxcontrol.png "CUIT_Phone_MapTextBoxControl")  
  
6.  Создайте код для изменений карты элементов управления ИП.  
  
     ![Формирование кода из построителя](../test/media/cuit-phone-generatecode.png "CUIT_Phone_GenerateCode")  
  
7.  С помощью перекрестья выберите текстовое поле, а затем свойство **Text** .  
  
     ![Выбор свойства Text](../test/media/cuit-phone-textproperty.png "CUIT_Phone_TextProperty")  
  
8.  Добавьте утверждение. Оно будет использоваться для проверки значения.  
  
     ![Добавление утверждения в тест](../test/media/cuit-phone-addassertion.png "CUIT_Phone_AddAssertion")  
  
9. Добавьте и создайте код для метода assert.  
  
     ![Формирование кода для утверждения](../test/media/cuit-phone-generatecodeassertion.png "CUIT_Phone_GenerateCodeAssertion")  
  
10. **Visual C#**  
  
     В обозревателе решений откройте файл UIMap.Designer.cs, чтобы просмотреть добавленный код для метода assert и элементов управления.  
  
     **Visual Basic**  
  
     В обозревателе решений откройте файл CodedUITest1.vb. В коде метода теста CodedUITestMethod1() щелкните правой кнопкой вызов метода assert, который был автоматически добавлен в `Me.UIMap.AssertMethod1()` , и выберите команду **Перейти к определению**. Файл UIMap.Designer.vb откроется в редакторе кода, где вы сможете просмотреть код, добавленный для метода assert и элементов управления.  
  
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
        Assert.AreEqual(this.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text);  
    }  
    ```  
  
    ```vb  
    Public Sub AssertMethod1()  
        Dim uITextBoxEdit As XamlEdit = Me.UIApp1Window.UITextBoxEdit  
  
        'Verify that the 'Text' property of 'textBox' text box equals 'button'  
        Assert.AreEqual(Me.AssertMethod1ExpectedValues.UITextBoxEditText, uITextBoxEdit.Text)  
    End Sub  
    ```  
  
     **Элементы управления**  
  
    ```csharp  
    #region Properties  
    public virtual AssertMethod1ExpectedValues AssertMethod1ExpectedValues  
    {  
        get  
        {  
            if ((this.mAssertMethod1ExpectedValues == null))  
            {  
                this.mAssertMethod1ExpectedValues = new AssertMethod1ExpectedValues();  
            }  
            return this.mAssertMethod1ExpectedValues;  
        }  
    }  
  
    public UIApp1Window UIApp1Window  
    {  
        get  
        {  
            if ((this.mUIApp1Window == null))  
            {  
                this.mUIApp1Window = new UIApp1Window();  
            }  
            return this.mUIApp1Window;  
        }  
    }  
    #endregion  
  
    #region Fields  
    private AssertMethod1ExpectedValues mAssertMethod1ExpectedValues;  
  
    private UIApp1Window mUIApp1Window;  
    #endregion  
    ```  
  
    ```vb  
    #Region "Properties"  
    Public ReadOnly Property UIButtonButton() As XamlButton  
        Get  
            If (Me.mUIButtonButton Is Nothing) Then  
                Me.mUIButtonButton = New XamlButton(Me)  
                Me.mUIButtonButton.SearchProperties(XamlButton.PropertyNames.AutomationId) = "button"  
            End If  
            Return Me.mUIButtonButton  
        End Get  
    End Property  
  
    Public ReadOnly Property UITextBoxEdit() As XamlEdit  
        Get  
            If (Me.mUITextBoxEdit Is Nothing) Then  
                Me.mUITextBoxEdit = New XamlEdit(Me)  
                Me.mUITextBoxEdit.SearchProperties(XamlEdit.PropertyNames.AutomationId) = "textBox"  
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
  
11. В обозревателе решений откройте файл CodedUITest1.cs или CodedUITest1.vb. Теперь вы можете добавить код в метод CodedUTTestMethod1 для действий, необходимых для выполнения теста. Используйте элементы управления, добавленные в UIMap, чтобы добавить код:  
  
    1.  Запустите приложение Windows Phone, используя свойство AutomationID, скопированное ранее в буфер обмена:  
  
        ```csharp  
        XamlWindow myAppWindow = XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App");  
        ```  
  
        ```vb  
        XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App");  
        ```  
  
    2.  Добавьте жест касания кнопки:  
  
        ```csharp  
        Gesture.Tap(this.UIMap.UIApp1Window.UIButtonButton);  
        ```  
  
        ```vb  
        Gesture.Tap(Me.UIMap.UIApp1Window.UIButtonButton)  
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
        XamlWindow myAppWindow = XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App");  
  
        // Tap the button.  
        Gesture.Tap(this.UIMap.UIApp1Window.UIButtonButton);  
  
        this.UIMap.AssertMethod1();  
    }  
    ```  
  
    ```vb  
    <CodedUITest>  
    Public Class CodedUITest1  
  
        <TestMethod()>  
        Public Sub CodedUITestMethod1()  
            '              
            ' To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.  
            '  
            ' Launch the app.  
            XamlWindow.Launch("ed85f6ff-2fd1-4ec5-9eef-696026c3fa7b_cyrqexqw8cc7c!App")  
  
            '// Tap the button.  
            Gesture.Tap(Me.UIMap.UIApp1Window.UIButtonButton)  
  
            Me.UIMap.AssertMethod1()  
        End Sub  
    ```  
  
## <a name="run-the-coded-ui-test"></a>Запустите закодированный тест пользовательского интерфейса.  
  
1.  Выполните построение теста и запустите его в обозревателе тестов.  
  
     ![Сборка и запуск теста с помощью обозревателя тестов](../test/media/cuit-phone-runtestexplorer.png "CUIT_Phone_RunTestExplorer")  
  
     Приложение Windows Phone запустится, будет выполнено действие касания кнопки, а свойство Text текстового поля будет заполнено и проверено с помощью метода assert.  
  
     ![Запуск теста Windows Phone](../test/media/cuit-phone-runtestexplorerrunning.png "CUIT_Phone_RunTestExplorerRunning")  
  
     После завершения теста обозреватель тестов подтвердит, что тест был пройден.  
  
     ![Результаты в обозревателе тестов](../test/media/cuit-phone-runtestexplorerresults.png "CUIT_Phone_RunTestExplorerResults")  
  
##  <a name="TestingPhoneAppsCodedUI_DataDriven"></a> Использование закодированных тестов пользовательского интерфейса на основе данных для приложений Windows Phone  
 Для проверки различных условий закодированный тест ИП можно запускать несколько раз с различными наборами данных.  
  
 Закодированные тесты ИП на основе данных для Windows Phone определяются с помощью атрибута DataRow тестового метода. В следующем примере для x и y заданы значения 1 и 2 в первой итерации и значения -1 и -2 во второй итерации теста.  
  
```  
[DataRow(1, 2, DisplayName = "Add positive numbers")]  
[DataRow(-1, -2, DisplayName = "Add negative numbers")]  
[TestMethod]  
public void DataDrivingDemo_MyTestMethod(int x, int y)  
  
```  
  
## <a name="q--a"></a>Вопросы и ответы  
  
### <a name="q-do-i-have-to-deploy-the-windows-phone-app-in-the-emulator-in-order-to-map-ui-controls"></a>В. Требуется ли развернуть приложение Windows Phone в эмуляторе для сопоставления элементов управления ИП?  
 **О**. Да, для использования построителя закодированных тестов ИП необходимо запустить эмулятор и развернуть в нем приложение. В противном случае появится сообщение о том, что запущенный эмулятор не найден.  
  
###  <a name="TestingPhoneAppsCodedUI_EmulatorDevice"></a> В. Тесты можно выполнять только на эмуляторе или можно использовать и физическое устройство?  
 **О**. Поддерживаются оба варианта. Цель выполнения теста выбирается за счет изменения типа эмулятора или устройства панели инструментов устройства. Если выбран параметр "Устройство", необходимо подключить устройство Phone Blue к одному из USB-портов компьютера.  
  
 ![Выбор версии эмулятора или физического устройства](../test/media/cuit-phone-testtarget.png "CUIT_Phone_TestTarget")  
  
### <a name="q-why-dont-i-see-the-option-to-record-my-coded-ui-test-in-the-generate-code-for-a-coded-ui-test-dialog"></a>В. Почему я не вижу параметр для записи закодированного теста ИП в диалоговом окне "Создать код" или "Закодированный тест ИП"?  
 **О**. Параметр записи не поддерживается для приложений Windows Phone.  
  
### <a name="q-can-i-create-a-coded-ui-test-for-my-windows-phone-apps-based-on-winjs-silverlight-or-html5"></a>В. Можно ли создать закодированный тест ИП для приложений Windows Phone, написанных на WinJS, Silverlight или HTML5?  
 **О**. Поддерживаются только приложения на XAML.  
  
### <a name="q-can-i-create-coded-ui-tests-for-my-windows-phone-apps-on-a-system-that-is-not-running-windows-81-or-windows-10"></a>В. Можно ли создать закодированные тесты пользовательского интерфейса для приложений Windows Phone в системе, не работающей под управлением Windows 8.1 или Windows 10?  
 **О**. Нет. Шаблоны проекта закодированного теста пользовательского интерфейса доступны только для Windows 8.1 и Windows 10. Чтобы создать автоматизацию для приложений универсальной платформы Windows (UWP), потребуется Windows 10.  

<a name="uwpapps"></a>  
### <a name="q-how-do-i-create-coded-ui-tests-for-universal-windows-platform-uwp-apps"></a>В. Как создать закодированные тесты ИП для приложений универсальной платформы Windows (UWP)?  
 **О**. В зависимости от платформы, на которой выполняется тестирование приложения UWP, создание проекта закодированного теста ИП осуществляется одним из следующих способов.  
  
-   Приложение UWP, работающее на локальном компьютере, будет выполняться как приложение для Магазина. Чтобы проверить это, необходимо использовать шаблон **проекта закодированного теста ИП (Windows)** . Чтобы найти этот шаблон при создании нового проекта, перейдите к узлу **Windows**, **Универсальный** . Или перейдите к узлу **Windows**, **Windows 8**, **Windows** .  
  
-   Приложение UWP, работающее на мобильном устройстве или в эмуляторе, будет выполняться как приложение Windows Phone. Чтобы проверить это, необходимо использовать шаблон **проекта закодированного теста ИП (Windows Phone)** . Чтобы найти этот шаблон при создании нового проекта, перейдите к узлу **Windows**, **Универсальный** . Или перейдите к узлу **Windows**, **Windows 8**, **Windows Phone** .  
  
 После создания проекта разработка теста остается прежней.  
  
### <a name="q-can-i-select-controls-that-are-outside-the-emulator"></a>В. Можно ли выбрать элементы управления вне эмулятора?  
 **О**. Нет, построитель их не определит.  
  
### <a name="q-can-i-use-the-coded-ui-test-builder-to-map-controls-using-a-physical-phone-device"></a>В. Можно ли с помощью построителя закодированных тестов ИП сопоставить элементы управления, используя физическое устройство?  
 **О**. Нет, построитель может сопоставить элементы ИП, только если приложение развернуто в эмуляторе.  
  
### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>В. Почему не следует изменять файл UIMap.Designer?  
 **О**. Любые изменения кода, внесенные в файл UIMapDesigner.cs, будут перезаписываться каждый раз при создании кода с помощью построителя кодированных тестов ИП. Если требуется изменить записанный метод, необходимо скопировать его в файл UIMap.cs и переименовать. Файл UIMap.cs можно использовать для переопределения методов и свойств в файле UIMapDesigner.cs. Необходимо удалить ссылку на исходный метод в файле CodedUITest.cs и заменить ее именем переименованного метода.  
  
### <a name="q-can-i-run-a-coded-ui-test-on-my-windows-phone-app-from-the-command-line"></a>В. Можно ли выполнять закодированный тест ИП для приложения Windows Phone из командной строки?  
 **О**. Да, используйте файл runsettings, чтобы указать целевое устройство для выполнения теста. Пример:  
  
 **vstest.console.exe "pathToYourCodedUITestDll" /settings:devicetarget.runsettings**  
  
 Пример RUNSETTINGS-файла:  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<RunSettings>  
<MSPhoneTest>  
<!--to specify test execution on device, use a TargetDevice option as follows-->  
<TargetDevice>Device</TargetDevice>  
<!--to specify an emulator instead, use a TargetDevice option like below-->  
<!--<TargetDevice>Emulator 8.1 WVGA 4 inch 512MB</TargetDevice>-->  
</MSPhoneTest>  
</RunSettings>  
```  
  
### <a name="q-what-are-the-differences-between-coded-ui-tests-for-xaml-based-windows-store-apps-and-windows-phone-apps"></a>В. В чем отличия закодированных тестов ИП для XAML-приложений Магазина Windows и приложений Windows Phone?  
 **О**. Существуют следующие основные различия.  
  
|Функция|Приложения для Магазина Windows|Приложения Windows Phone|  
|-------------|------------------------|------------------------|  
|Цель для запуска тестов|Локальный или удаленный компьютер. Удаленные компьютеры можно указать при использовании автоматизированного тестового случая для выполнения тестов. См. раздел [Автоматизация тестового случая в Microsoft Test Manager](http://msdn.microsoft.com/library/4e02568b-9cde-47cc-b41c-82726c177e42).|Эмулятор или устройство. См. раздел [В. Тесты можно выполнять только на эмуляторе или можно использовать и физическое устройство?](#TestingPhoneAppsCodedUI_EmulatorDevice) ранее.|  
|Выполнение из командной строки|Файл параметров не требуется для указания цели.|Для указания цели требуется файл Runsettings.|  
|Специализированные классы для элементов управления оболочки|<xref:Microsoft.VisualStudio.TestTools.UITesting.DirectUIControls.DirectUIControl>|<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl>|  
|Элемент управления WebView в XAML-приложении|Поддерживается, если вы используете специализированные классы Html* для взаимодействия с элементами HTML. См. раздел <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>.|Не поддерживается.|  
|Выполнение автоматизированных тестов в MTM|Поддерживается.|Не поддерживается.|  
|Тесты на основе данных|Сведения об использовании внешних источников данных и атрибута DataSource тестового метода см. в разделе [Тесты на основе данных](../test/creating-a-data-driven-coded-ui-test.md) .|Данные указываются в строке с использованием атрибута DataRow тестового метода. См. раздел [Использование закодированных тестов ИП на основе данных для приложений Windows Phone](#TestingPhoneAppsCodedUI_DataDriven) этой статьи.|  
  
## <a name="external-resources"></a>Внешние ресурсы  
 Блог Microsoft Visual Studio Application Lifecycle Management: [Использование закодированных тестов пользовательского интерфейса для проверки XAML-приложений Windows Phone](http://blogs.msdn.com/b/visualstudioalm/archive/2014/04/05/using-coded-ui-to-test-xaml-based-windows-phone-apps.aspx?PageIndex=2#comments)  
  
## <a name="see-also"></a>См. также  
 [Использование модели автоматизации пользовательского интерфейса для тестирования кода](../test/use-ui-automation-to-test-your-code.md)



