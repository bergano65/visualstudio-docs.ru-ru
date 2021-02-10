---
title: Создание надстройки для средства просмотра результатов веб-тестов производительности
description: Сведения о том, как создать надстройку Visual Studio для расширения возможностей, предоставляемых пользовательским интерфейсом в средстве просмотра результатов веб-тестов производительности, и реализации классов, необходимых для расширения пользовательского интерфейса.
ms.custom: SEO-VS-2020
ms.date: 10/20/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, Visual Studio Add-in
- Visual Studio Add-in, Web performance tests
ms.assetid: 1118c604-4b1b-4b21-a04e-45995b676fa8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: e2773165b37600eb214893de91f8fc8c4467c0d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937632"
---
# <a name="how-to-create-an-add-in-for-the-web-performance-test-results-viewer"></a>Практическое руководство. Создание надстройки для средства просмотра результатов веб-тестов производительности

Пользовательский интерфейс **средства просмотра результатов веб-тестов производительности** можно расширить с помощью следующих пространств имен:

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>

Кроме того, необходимо добавить ссылку на DLL-файл LoadTestPackage, расположенный в папке *%ProgramFiles(x86)%\Microsoft Visual Studio\\\<version>\Enterprise\Common7\IDE\PrivateAssemblies*.

Чтобы расширить интерфейс **средства просмотра результатов веб-тестов производительности**, необходимо создать надстройку Visual Studio и добавить пользовательский элемент управления. Ниже описано, как создать надстройку и пользовательский элемент управления, а также как реализовать классы, необходимые для расширения пользовательского интерфейса **средства просмотра результатов веб-тестов производительности**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="create-or-open-a-solution-that-contains-an-aspnet-web-application-and-a-web-performance-and-load-test-project"></a>Создание и открытие решения, содержащего веб-приложение ASP.NET и проект веб-тестов производительности и нагрузочных тестов

### <a name="to-prepare-for-extending-the-web-performance-test-results-viewer"></a>Подготовка к расширению средства просмотра результатов веб-тестов производительности

Создайте или откройте решение, не находящееся в рабочей среде, с которым можно экспериментировать и которое содержит веб-приложение ASP.NET и проект веб-тестов производительности и нагрузочных тестов с одним или несколькими веб-тестами производительности для этого веб-приложения ASP.NET.

> [!NOTE]
> Веб-приложение ASP.NET и проект веб-тестов производительности и нагрузочного теста, содержащий веб-тесты производительности, можно создать с помощью процедур, описанных в разделах [Практическое руководство. Создание теста веб-службы](../test/how-to-create-a-web-service-test.md) и [Создание и запуск закодированного веб-теста производительности](../test/generate-and-run-a-coded-web-performance-test.md).

## <a name="create-a-visual-studio-add-in"></a>Создание надстройки Visual Studio

Надстройка представляет собой скомпилированную библиотеку DLL, запускаемую в интегрированной среде разработки Visual Studio. Компиляция обеспечивает защиту интеллектуальной собственности и повышает производительность. Хотя надстройки можно создавать вручную, удобнее делать это с помощью **мастера надстроек**. Мастер создает функциональную, но простую надстройку, которая может быть запущена сразу же после создания. После создания базовой пустой программы **мастером надстроек** ее можно настраивать и добавлять в нее код.

**Мастер надстроек** позволяет задавать для надстройки отображаемое имя и описание. Они появятся в диалоговом окне **Диспетчер надстроек**. Кроме того, можно указать, чтобы мастер создавал код, добавляющий в меню **Сервис** команду для открытия надстройки. Можно также выбрать пользовательское диалоговое окно **О программе**, которое будет отображаться для надстройки. По выполнении шагов мастера будет создан новый проект с единственным классом, который реализует надстройку. Этот класс имеет имя Connect.

**Диспетчер надстроек** понадобится в конце статьи.

### <a name="to-create-an-add-in-by-using-the-add-in-wizard"></a>Чтобы создать надстройку с помощью мастера надстроек

1. В **обозревателе решений** щелкните правой кнопкой мыши решение, выберите команду **Добавить** и пункт **Новый проект**.

2. Создайте проект **Надстройка Visual Studio**.

    Будет запущен **мастер надстроек** Visual Studio.

3. Нажмите кнопку **Далее**.

4. На странице **Выбрать язык программирования** выберите язык программирования, который предполагается использовать для написания надстройки.

   > [!NOTE]
   > Примеры кода в этом разделе написаны на языке Visual C#.

5. На странице **Выберите ведущее приложение** выберите пункт **Visual Studio** и снимите флажок **Макросы Visual Studio**.

6. Нажмите кнопку **Далее**.

7. Введите имя и описание надстройки на странице **Ввести имя и описание**.

     После создания надстройки ее имя и описание выводятся в списке **Имеющиеся надстройки** диалогового окна **Диспетчер надстроек**. Создайте достаточно подробное описание надстройки так, чтобы пользователи могли узнать, что делает надстройка, как она работает и так далее.

8. Нажмите кнопку **Далее**.

9. На странице **Выберите параметры надстроек** выберите **Загружать надстройку во время запуска ведущего приложения**.

10. Снимите оставшиеся флажки.

11. На странице **Выберите "Справка. О программе"** можно указать, должна ли информация о надстройке отображаться в диалоговом окне **О программе**. Если эта информация должна отображаться, установите флажок **Да, пусть надстройка содержит диалоговое окно "О программе"** .

     В сведениях, отображаемых в диалоговом окне **About** Visual Studio, можно указать номер версии, сведения о поддержке, данные о лицензии и т. д.

12. Нажмите кнопку **Далее**.

13. Выбранные параметры будут показаны на странице **Сводка** для проверки. Если все верно, нажмите кнопку **Готово**, чтобы создать надстройку. Если необходимо что-либо изменить, нажмите кнопку **Назад**.

     Будут созданы проект и решение, а файл *Connect.cs* новой надстройки появится в **редакторе кода**.

     Код в файл *Connect.cs* будет добавлен после выполнения следующей процедуры, создающей пользовательский элемент управления, ссылка на который будет содержаться в проекте WebPerfTestResultsViewerAddin.

    После создания надстройки ее нужно зарегистрировать в Visual Studio, прежде чем ее можно будет активировать, используя **Диспетчер надстроек**. Для этого используется XML-файл с расширением имени файла *ADDIN*.

    Этот файл с расширением *ADDIN* содержит описание сведений, необходимых Visual Studio для отображения надстройки в окне **Диспетчер надстроек**. При запуске Visual Studio выполняется поиск доступных файлов *ADDIN* в соответствующем расположении. При нахождении такого файла XML-файл считывается, и в окно **Диспетчер надстроек** передаются сведения, необходимые для запуска надстройки по щелчку мыши.

    Файл с расширением *ADDIN* создается автоматически вместе с надстройкой **мастером надстроек**.

### <a name="add-in-file-locations"></a>Добавление расположений файлов

**Мастер надстроек** автоматически создает две копии файла с расширением *ADDIN* указанным ниже образом.

|**Расположение файла с расширением ADDIN**|**Описание**|
|-|----------------------------|-|
|Корневая папка проекта|Используется для развертывания проекта надстройки. Включается в проект для простоты редактирования и имеет локальный путь для развертывания в стиле XCopy.|
|Папка надстройки|Используется для запуска надстройки в среде отладки. Должна всегда указывать на выходной путь текущей конфигурации построения.|

## <a name="create-a-windows-form-control-library-project"></a>Создание проекта библиотеки элементов управления Windows Forms

Созданная выше надстройка Visual Studio ссылается на проект библиотеки элементов управления Windows Forms для создания экземпляра класса <xref:System.Windows.Forms.UserControl>.

### <a name="to-create-a-control-to-be-used-in-the-web-test-results-viewer"></a>Создание элемента управления, который будет использоваться в средстве просмотра результатов веб-тестов

1. В **обозревателе решений** щелкните правой кнопкой мыши решение, выберите команду **Добавить** и пункт **Новый проект**.

2. Создайте проект **Библиотека элементов управления Windows Forms**.

3. С **панели элементов** перетащите элемент <xref:System.Windows.Forms.DataGridView> на форму userControl1.

4. Щелкните глиф тега действий (![глиф смарт-тега](../test/media/vs_winformsmttagglyph.gif)) в правом верхнем углу элемента управления <xref:System.Windows.Forms.DataGridView> и выполните следующие действия.

    1. Выберите **Закрепить в родительском контейнере**.

    2. Снимите флажки **Разрешить добавление**, **Разрешить изменение**, **Разрешить удаление** и **Разрешить изменение порядка столбцов**.

    3. Выберите пункт **Добавить столбец**.

         Откроется диалоговое окно **Добавление столбца**.

    4. В раскрывающемся списке **Тип** выберите вариант **DataGridViewTextBoxColumn**.

    5. Удалите текст "Column1" из поля **Текст заголовка**.

    6. Выберите **Добавить**.

    7. Нажмите кнопку **Закрыть**.

5. В окне **Свойства** измените свойство **(Name)** объекта <xref:System.Windows.Forms.DataGridView> на **resultControlDataGridView**.

6. Щелкните правой кнопкой мыши область конструктора и выберите команду **Просмотреть код**.

     В **редакторе кода** будет открыт файл *UserControl1.cs*.

7. Измените имя созданного экземпляра класса <xref:System.Windows.Forms.UserControl> с UserContro1 на resultControl:

    ```csharp
    namespace WebPerfTestResultsViewerControl
    {
        public partial class resultControl : UserControl
        {
            public resultControl()
            {
                InitializeComponent();
            }
    ```

     В следующей процедуре в файл *Connect.cs* проекта WebPerfTestResultsViewerAddin будет добавлен код, ссылающийся на класс resultControl.

     Позже в файл *Connect.cs* будет добавлен дополнительный код.

## <a name="add-code-to-the-webperftestresultsvieweraddin"></a>Добавление кода в файл WebPerfTestResultsViewerAddin

1. В **обозревателе решений** щелкните правой кнопкой мыши узел **Ссылки** в проекте WebPerfTestResultsViewerAddin и выберите команду **Добавить ссылку**.

2. В диалоговом окне **Добавить ссылку** выберите вкладку **.NET**.

3. Прокрутите список вниз и выберите **Microsoft.VisualStudio.QualityTools.WebTestFramework** и **System.Windows.Forms**.

4. Нажмите кнопку **ОК**.

5. Снова щелкните правой кнопкой мыши узел **Ссылки** и выберите команду **Добавить ссылку**.

6. В диалоговом окне **Добавление ссылки** перейдите на вкладку **Обзор**.

7. Выберите раскрывающийся список **Поиск в**, перейдите в папку *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies* и выберите файл *Microsoft.VisualStudio.QualityTools.LoadTestPackage.dll*.

8. Нажмите кнопку **ОК**.

9. Щелкните правой кнопкой мыши узел проекта WebPerfTestResultsViewerAddin и выберите команду **Добавить ссылку**.

10. В диалоговом окне **Добавление ссылки** перейдите на вкладку **Проекты**.

11. В списке **Имя проекта** выберите проект **WebPerfTestResultsViewerControl** и нажмите кнопку **ОК**.

12. Если файл *Connect.cs* еще не открыт, в **обозревателе решений** щелкните правой кнопкой мыши файл **Connect.cs** в проекте WebPerfTestResultsViewerAddin и выберите команду **Просмотреть код**.

13. Добавьте в файл *Connect.cs* следующие инструкции:

    ```csharp
    using System.IO;
    using System.Windows.Forms;
    using System.Collections.Generic;
    using Microsoft.VisualStudio.TestTools.LoadTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using WebPerfTestResultsViewerControl;
    ```

14. Прокрутите в конец файла *Connect.cs*. Если открыто более одного экземпляра **средства просмотра результатов веб-тестов производительности**, необходимо добавить список GUID для <xref:System.Windows.Forms.UserControl>. Позже будет добавлен код, использующий этот список.

     Второй список строк используется в методе OnDiscconection, код которого будет написан позже.

    ```csharp
    private DTE2 _applicationObject;
    private AddIn _addInInstance;

    private Dictionary<Guid, List<UserControl>> m_controls = new Dictionary<Guid, List<UserControl>>();        private List<string> temporaryFilePaths = new List<string>();
    ```

15. Файл *Connect.cs* создает экземпляр класса Connect из класса <xref:Extensibility.IDTExtensibility2>, а также содержит некоторые методы, необходимые для реализации надстройки Visual Studio. Один из этих методов — OnConnection, который получает уведомление о том, что надстройка загружена. В методе OnConnection будет использоваться класс LoadTestPackageExt, чтобы создать пакет расширяемости для **средства просмотра результатов веб-тестов производительности**. Добавьте следующий код в метод OnConnection:

    ```csharp
    public void OnConnection(object application, ext_ConnectMode connectMode, object addInInst, ref Array custom)
                {
                _applicationObject = (DTE2)application;
                _addInInstance = (AddIn)addInInst;

                // Create a load test packge extensibility class.            LoadTestPackageExt loadTestPackageExt = _applicationObject.GetObject("Microsoft.VisualStudio.TestTools.LoadTesting.LoadTestPackageExt") as LoadTestPackageExt;            // Process open windows.            foreach (WebTestResultViewer webTestResultViewer in loadTestPackageExt.WebTestResultViewerExt.ResultWindows)            {                WindowCreated(webTestResultViewer);            }            // Create event handlers.            loadTestPackageExt.WebTestResultViewerExt.WindowCreated += new EventHandler<WebTestResultViewerExt.WindowCreatedEventArgs>(WebTestResultViewerExt_WindowCreated);            loadTestPackageExt.WebTestResultViewerExt.WindowClosed += new EventHandler<WebTestResultViewerExt.WindowClosedEventArgs>(WebTesResultViewer_WindowClosed);            loadTestPackageExt.WebTestResultViewerExt.SelectionChanged += new EventHandler<WebTestResultViewerExt.SelectionChangedEventArgs>(WebTestResultViewer_SelectedChanged);
            }
    ```

16. Добавьте следующий код в класс Connect, чтобы создать метод WebTestResultViewerExt_WindowCreated для обработчика событий loadTestPackageExt.WebTestResultViewerExt.WindowCreated, добавленного в метод OnConnection, и для метода WindowCreated, вызываемого методом WebTestResultViewerExt_WindowCreated.

    ```csharp
            void WebTestResultViewerExt_WindowCreated(object sender, WebTestResultViewerExt.WindowCreatedEventArgs e)
            {
                // New control added to new result viewer window.
                WindowCreated(e.WebTestResultViewer);
            }

    private void WindowCreated(WebTestResultViewer viewer)        {            // Instantiate an instance of the resultControl referenced in the WebPerfTestResultsViewerControl project.
                resultControl resultControl = new resultControl();            // Add to the dictionary of open playback windows.            System.Diagnostics.Debug.Assert(!m_controls.ContainsKey(viewer.TestResultId));            List<UserControl> userControls = new List<UserControl>();            userControls.Add(resultControl);            // Add Guid to the m_control List to manage Result viewers and controls.            m_controls.Add(viewer.TestResultId, userControls);            // Add tabs to the playback control.            resultControl.Dock = DockStyle.Fill;            viewer.AddResultPage(new Guid(), "Sample", resultControl);        }
    ```

17. Добавьте следующий код в класс Connect, чтобы создать метод WebTestResultViewer_SelectedChanged для обработчика событий loadTestPackageExt.WebTestResultViewerExt.SelectionChanged, добавленного в метод OnConnection:

    ```csharp
    void WebTestResultViewer_SelectedChanged(object sender, WebTestResultViewerExt.SelectionChangedEventArgs e)
    {
        foreach (UserControl userControl in m_controls[e.TestResultId])            {                // Update the userControl in each result viewer.                resultControl resultControl = userControl as resultControl;                if (resultControl != null)                    // Call the resultControl's Update method (This will be added in the next procedure).                    resultControl.Update(e.WebTestRequestResult);            }
    }
    ```

18. Добавьте следующий код в класс Connect, чтобы создать метод WebTesResultViewer_WindowClosed для обработчика событий loadTestPackageExt.WebTestResultViewerExt.WindowClosed, добавленного в метод OnConnection:

    ```csharp
    void WebTesResultViewer_WindowClosed(object sender, WebTestResultViewerExt.WindowClosedEventArgs e)
    {
        if (m_controls.ContainsKey(e.WebTestResultViewer.TestResultId))
        {
            m_controls.Remove(e.WebTestResultViewer.TestResultId);
        }
    }
    ```

     После завершения создания кода надстройки для Visual Studio необходимо добавить метод Update в класс resultControl в проекте WebPerfTestResultsViewerControl.

## <a name="add-code-to-the-webperftestresultsviewercontrol"></a>Добавление кода в проект WebPerfTestResultsViewerControl

1. В **обозревателе решений** щелкните правой кнопкой мыши узел проекта WebPerfTestResultsViewerControl и выберите пункт **Свойства**.

2. Перейдите на вкладку **Приложение**, в раскрывающемся списке **Целевая платформа** выберите **.NET Framework 4** (или более позднюю версию). Закройте окно **Свойства**.

   Это требуется сделать для поддержки ссылок на DLL-файлы, необходимые для расширения **средства просмотра результатов веб-тестов производительности**.

3. В **обозревателе решений** в проекте WebPerfTestResultsViewerControl щелкните правой кнопкой мыши узел **Ссылки** и выберите команду **Добавить ссылку**.

4. В диалоговом окне **Добавить ссылку** выберите вкладку **.NET**.

5. Прокрутите вниз и выберите **Microsoft.VisualStudio.QualityTools.WebTestFramework**.

6. Нажмите кнопку **ОК**.

7. Добавьте в файл *UserControl1.cs* следующие операторы:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting.Rules;
    ```

8. Добавьте метод Update, который вызывается методом WebTestResultViewer_SelectedChanged WebPerfTestResultsViewerAddin в файле *Connect.cs* и принимает объект WebTestRequestResult. Метод Update заполняет DataGridView различными свойствами, переданными в объекте WebTestRequestResult.

    ```csharp
    public void Update(WebTestRequestResult WebTestResults)
            {
                // Clear the DataGridView when a request is selected.
                resultControlDataGridView.Rows.Clear();
                // Populate the DataGridControl with properties from the WebTestResults.
                this.resultControlDataGridView.Rows.Add("Request: " + WebTestResults.Request.Url.ToString());
                this.resultControlDataGridView.Rows.Add("Response: " + WebTestResults.Response.ResponseUri.ToString());
                foreach (RuleResult ruleResult in WebTestResults.ExtractionRuleResults)
                {
                    this.resultControlDataGridView.Rows.Add("Extraction rule results: " + ruleResult.Message.ToString());
                }
                foreach (RuleResult ruleResult in WebTestResults.ValidationRuleResults)
                {
                    this.resultControlDataGridView.Rows.Add("Validation rule results: " + ruleResult.Message.ToString());
                }
                foreach (WebTestError webTestError in WebTestResults.Errors)
                {
                    this.resultControlDataGridView.Rows.Add("Error: " + webTestError.ErrorType.ToString() + " " + webTestError.ErrorSubtype.ToString() + " " + webTestError.ExceptionText.ToString());
                }
            }
    ```

## <a name="build-the-solution"></a>Построение решения

- В меню **Сборка** выберите команду **Собрать решение**.

## <a name="register-the-webperftestresultsvieweraddin-add-in"></a>Регистрация надстройки WebPerfTestResultsViewerAddin

1. В меню **Сервис** выберите пункт **Диспетчер надстроек**.

2. Откроется диалоговое окно **Диспетчер надстроек**.

3. В столбце **Имеющиеся надстройки** установите флажок для надстройки WebPerfTestResultsViewerAddin и снимите флажки в столбцах **Запуск** и **Командная строка**.

4. Нажмите кнопку **ОК**.

## <a name="run-the-web-performance-test-using-the-web-test-results-viewer"></a>Запуск веб-теста производительности с помощью средства просмотра результатов веб-тестов производительности

1. Запустите веб-тест производительности. При этом в **средстве просмотра веб-тестов производительности** появится вкладка надстройки WebPerfTestResultsViewerAddin, имеющая название Sample.

2. Перейдите на эту вкладку, чтобы увидеть свойства, отображаемые в DataGridView.

## <a name="net-security"></a>Безопасность в .NET

Для повышения безопасности за счет предотвращения автоматической активации вредоносных надстроек в Visual Studio на странице **Сервис -> Параметры** имеются параметры **Безопасность надстроек и макросов**.

Кроме того, на странице "Параметры" можно указать, в каких папках Visual Studio осуществляет поиск *ADDIN*-файлов регистрации. Это повышает безопасность путем ограничения числа папок, из которых может осуществляться чтение *ADDIN*-файлов регистрации. Кроме того, это позволяет защититься от непреднамеренного использования вредоносных *ADDIN*-файлов.

**Параметры безопасности надстроек**

Безопасность надстроек определяется следующими параметрами:

- **Разрешить загрузку компонентов надстроек**. По умолчанию выбрано. Если этот параметр выбран, загрузка надстроек в Visual Studio разрешена. Если этот параметр не выбран, загрузка надстроек в Visual Studio запрещена.

- **Разрешить загрузку компонентов надстроек с URL-адреса**. По умолчанию не выбрано. Если этот параметр выбран, надстройки могут загружаться с внешних веб-сайтов. Если этот параметр не выбран, загрузка удаленных надстроек в Visual Studio запрещена. Если по некоторым причинам надстройка не загружается, ее невозможно загрузить из Интернета. Этот параметр влияет только на загрузку DLL надстройки. Файлы регистрации *ADDIN* всегда должны быть расположены в локальной системе.

## <a name="see-also"></a>См. также

- <xref:System.Windows.Forms.UserControl>
- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.DataGrid>
- [Создание пользовательского кода и подключаемых модулей для нагрузочных тестов](../test/create-custom-code-and-plug-ins-for-load-tests.md)
