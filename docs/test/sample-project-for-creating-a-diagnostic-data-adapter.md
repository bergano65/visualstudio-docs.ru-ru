---
title: Пример проекта для создания адаптера диагностических данных в Visual Studio | Документы Майкрософт
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- samples. Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter, sample
ms.assetid: 548bdc5e-338f-4be7-a555-e6a2efb1df6b
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 98606c5afbeed035392f35d71de60bb4d4bbb5a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sample-project-for-creating-a-diagnostic-data-adapter"></a>Пример проекта для создания адаптера диагностических данных

"MyDiagnosticDataAdapter" — это простой адаптер диагностических данных, который может вкладывать файл журнала в результаты теста при выполнении тестов.

 Потребуются административные разрешения на всех компьютерах, на которых установлен сборщик диагностических данных или редактор конфигурации.

## <a name="example-data-adapter"></a>Пример адаптера данных

В этом примере показано выполнение следующих задач.

-   Применение атрибутов, чтобы класс мог быть обнаружен Microsoft Test Manager как адаптер диагностических данных.

-   Применение атрибутов, чтобы класс пользовательского элемента управления мог быть обнаружен Microsoft Test Manager как редактор, используемый для изменения конфигурации для адаптера диагностических данных.

-   Доступ к данным конфигурации по умолчанию.

-   Регистрация определенных событий сбора диагностических данных.

-   Вложение файла журнала посредством его отправки в <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink>.

```csharp
// My Data Collector Class
using Microsoft.VisualStudio.TestTools.Common;
using Microsoft.VisualStudio.TestTools.Execution;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Xml;
using System;

namespace MyCompany.MyDiagnosticDataAdapters
{
    // Provide a URI and friendly name for your diagnostic data adapter
    [DataCollectorTypeUri("datacollector://MyCompany/MyDataCollector/1.0")]
    [DataCollectorFriendlyName("Collect Log Files sample", false)]
    // Designate your chosen configuration editor
    [DataCollectorConfigurationEditor(
        "configurationeditor://MyCompany/MyDataConfigEditor/1.0")]
    public class MyDataCollector : DataCollector
    {
        private DataCollectionEvents dataEvents;
        private DataCollectionLogger dataLogger;
        private DataCollectionSink dataSink;
        private XmlElement configurationSettings;

        // Required method called by the testing framework
        public override void Initialize(
            XmlElement configurationElement,
            DataCollectionEvents events,
            DataCollectionSink sink,
            DataCollectionLogger logger,
            DataCollectionEnvironmentContext environmentContext)
        {
            dataEvents = events; // The test events
            dataLogger = logger; // The error and warning log
            dataSink = sink;     // Saves collected data
            // Configuration from the test settings
            configurationSettings = configurationElement;

            // Register common events for the data collector
            // Not all of the events are used in this class
            dataEvents.SessionStart +=
                new EventHandler<SessionStartEventArgs>(OnSessionStart);
            dataEvents.SessionEnd +=
                new EventHandler<SessionEndEventArgs>(OnSessionEnd);
            dataEvents.TestCaseStart +=
                new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
            dataEvents.TestCaseEnd +=
                new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
            dataEvents.DataRequest +=
                new EventHandler<DataRequestEventArgs>(OnDataRequest);
        }

        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                dataEvents.SessionStart -=
                    new EventHandler<SessionStartEventArgs>(OnSessionStart);
                dataEvents.SessionEnd -=
                    new EventHandler<SessionEndEventArgs>(OnSessionEnd);
                dataEvents.TestCaseStart -=
                    new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
                dataEvents.TestCaseEnd -=
                    new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
                dataEvents.DataRequest -=
                    new EventHandler<DataRequestEventArgs>(OnDataRequest);
            }
        }

        #region Event Handlers
        public void OnSessionStart(object sender, SessionStartEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnSessionEnd(object sender, SessionEndEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnTestCaseStart(object sender, TestCaseEventArgs e)
        {
            // TODO: Provide implementation
        }

        public void OnTestCaseEnd(object sender, TestCaseEndEventArgs e)
        {
            // Get any files to be collected that are
            // configured in your test settings
            List<string> files = getFilesToCollect();

            // For each of the files, send the file to the data sink
            // which will attach it to the test results or to a bug
            foreach (string file in files)
            {
                dataSink.SendFileAsync(e.Context, file, false);
            }
        }

        public void OnDataRequest(object sender, DataRequestEventArgs e)
        {
            // TODO: Provide implementation
            // Most likely this occurs because a bug is being filed
        }
        #endregion

        // A private method to collect the configured file names
        private List<string> getFilesToCollect()
        {
            // Seetup namespace manager with our namespace
            XmlNamespaceManager nsmgr =
                new XmlNamespaceManager(
                    configurationSettings.OwnerDocument.NameTable);
            nsmgr.AddNamespace("ns",
                "http://MyCompany/schemas/MyDataCollector/1.0");

            // Find all of the "File" elements under our configuration
            XmlNodeList files =
                configurationSettings.SelectNodes(
                    "//ns:MyDataCollector/ns:File");

            // Build the list of files to collect from the
            // "FullPath" attributes of the "File" nodes.
            List<string> result = new List<string>();
            foreach (XmlNode fileNode in files)
            {
                XmlAttribute pathAttribute =
                    fileNode.Attributes["FullPath"];
                if (pathAttribute != null &&
                    !String.IsNullOrEmpty(pathAttribute.Value))
                {
                    result.Add(pathAttribute.Value);
                }
            }

            return result;
        }
    }
}
```

## <a name="example-configuration-editor"></a>Пример редактора конфигурации

Это пример редактора конфигурации для адаптера диагностических данных. Добавьте в проект пользовательский элемент управления и создайте простую форму с меткой ("Имя файла журнала:") и текстовое поле с именем "FileTextBox".

```csharp
using Microsoft.VisualStudio.TestTools.Common;
using Microsoft.VisualStudio.TestTools.Execution;
using System.Collections.Generic;
using System.ComponentModel;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Windows.Forms;
using System.Xml;
using System;

namespace MyCompany.DiagnosticDataAdapters.ConfigurationEditors
{
    [DataCollectorConfigurationEditorTypeUri(
        "configurationeditor://MyCompany/MyConfigEditor/1.0")]
    public partial class MyDataConfigEditor :
        UserControl, IDataCollectorConfigurationEditor
    {
        private DataCollectorSettings collectorSettings;

        // Create a private property for the service provider
        private IServiceProvider ServiceProvider { get; set; }

        // Constructor
        public MyConfigurationEditor()
        {
            InitializeComponent();
        }

        // Required method called by the testing framework
        public void Initialize(
            IServiceProvider svcProvider,
            DataCollectorSettings settings)
        {
            ServiceProvider = svcProvider;
            collectorSettings = settings;

            // Display the file name as listed in the settings file.
            // If the configuration has not been updated before, this
            // data will be provided by the default configuration
            // section from <nameofcollector>.dll.config:
            // <DefaultConfiguration>
            //   <MyCollectorName
            //       xmlns="http://MyCompany/schemas/ProductName/Version");
            //     <File FullPath="C:\temp\logfile1.txt" />
            //   </MyCollectorName>
            // </DefaultConfiguration>
            this.SuspendLayout();
            this.FileTextBox.Text = GetText(collectorSettings.Configuration);
            this.ResumeLayout();
        }

        // Can be used to verify data before saving it
        public bool VerifyData()
        {
            // Not currently verifying data
            return true;
        }

        // Reset to default value from XML configuration
        // using a custom method
        public void ResetToAgentDefaults()
        {
            this.FileTextBox.Text =
                getText(collectorSettings.DefaultConfiguration);
        }

        // Saves data changed in the editor to the test configuration
        // settings. Does not change the default value.
        public DataCollectorSettings SaveData()
        {
            collectorSettings.Configuration.InnerXml =
                String.Format(
                    @"<MyCollectorName
      xmlns=""http://MyCompany/schemas/MyDataCollector/1.0"">
  <File FullPath=""{0}"" />
</MyCollectorName>",
                    FileTextBox.Text);
            return collectorSettings;
        }

        // Reads the configuration settings
        private string getText(XmlElement element)
        {
            // Setup namespace manager with our namespace
            XmlNamespaceManager nsmgr =
                new XmlNamespaceManager(
                    element.OwnerDocument.NameTable);

            // Find all the "File" elements under our configuration
            XmlNodeList files = element.SelectNodes("//ns:MyDataCollector/ns:File", nsmgr);

            string result = String.Empty;
            if (files.Count > 0)
            {
                XmlAttribute pathAttribute = files[0].Attributes["FullPath"];
                if (pathAttribute != null &&
                    !String.IsNullOrEmpty(pathAttribute.Value))
                {
                    result = pathAttribute.Value;
                }
            }

            return result;
        }
    }
}
```

## <a name="example-configuration-file"></a>Пример файла конфигурации

Далее приводится пример файла конфигурации для редактора конфигурации сборщика диагностических данных.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <section
      name="DataCollectorConfiguration"
      type="Microsoft.VisualStudio.QualityTools.Execution.DataCollectorConfigurationSection,
        Microsoft.visualStudio.QualityTools.ExecutionCommon,
        Version=4.0.0.0, Culture=neutral,
        PublicKeyToken=b03f5f7f11d50a3a" />
  </configSections>
  <DataCollectorConfiguration
      xmlns="http://microsoft.com/schemas/VisualStudio/TeamTest/11">
    <DataCollector
        typeUri="datacollector://MyCompany/MyDataCollector/1.0">
      <DefaultConfiguration>
        <!-- Your default config settings-->
        <File FullPath="c:\temp\logfile1.txt" />
      </DefaultConfiguration>
    </DataCollector>
  </DataCollectorConfiguration>
</configuration>

```

## <a name="compiling-the-code"></a>Компиляция кода

### <a name="to-create-the-code-project-for-this-diagnostic-adapter"></a>Для создания проекта кода для данного адаптера диагностических данных выполните следующие действия.

1.  Создайте новый проект библиотеки классов и назовите его "MyDataCollector".

2.  В **обозревателе решений** щелкните правой кнопкой мыши проект и выберите пункт **Свойства**. Чтобы выбрать добавляемую папку, выберите пункт **Пути для ссылок** и нажмите кнопку с многоточием (**…**).

     Появится диалоговое окно **Выбор пути для ссылок**.

3.  Выберите следующий путь (в зависимости от каталога установки): *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*. Нажмите кнопку **ОК**.

4.  Чтобы добавить папку к пути для ссылок, выберите команду **Добавить папку**.

     Папка отображается в списке путей для ссылок.

5.  Выберите значок **Сохранить все**, чтобы сохранить пути для ссылок.

6.  Добавьте сборку **Microsoft.VisualStudio.QualityTools.ExecutionCommon**.

    1.  В **обозревателе решений** щелкните правой кнопкой мыши пункт **Ссылки** и выберите команду **Добавить ссылку**.

    2.  Нажмите кнопку **Обзор** и найдите **Microsoft.VisualStudio.QualityTools.ExecutionCommon.dll**.

         Данная сборка находится в папке *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*.

    3.  Нажмите кнопку **ОК**.

7.  Добавьте сборку **Microsoft.VisualStudio.QualityTools.Common**.

    1.  В обозревателе решений щелкните правой кнопкой мыши пункт **Ссылки** и выберите команду **Добавить ссылку**.

    2.  Нажмите кнопку **Обзор** и найдите **Microsoft.VisualStudio.QualityTools.Common.dll**.

         Данная сборка находится в папке *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies*.

    3.  Нажмите кнопку **ОК**.

8.  Скопируйте класс адаптера диагностических данных, описанный ранее в этом документе, в класс библиотеки классов. Сохраните данный класс.

9. Для добавления в проект пользовательского элемента управления щелкните правой кнопкой мыши проект MyDataCollector в обозревателе решений и последовательно выберите пункты **Добавить** и **Пользовательский элемент управления**. Выберите **Добавить**.

10. С помощью панели элементов добавьте к пользовательскому элементу управления подпись и измените свойство "Text" на **Имя файла:**.

11. С помощью панели элементов добавьте в пользовательский элемент управления текстовое поле и измените имя на **textBoxFileName**.

12. В **обозревателе решений** щелкните правой кнопкой мыши пользовательский элемент управления и выберите команду **Просмотреть код**. Замените данный класс пользовательского элемента управления классом пользовательского элемента управления, описанным ранее в этом документе. Сохраните данный класс.

    > [!NOTE]
    > По умолчанию пользовательский элемент управления называется UserControl1. Убедитесь в том, что код класса пользовательского элемента управления использует имя вашего элемента управления.

13. Чтобы создать файл конфигурации, щелкните решение правой кнопкой мыши в **обозревателе решений** и последовательно выберите пункты **Добавить** и **Создать элемент**. Выберите пункт **Файл конфигурации приложения** и нажмите кнопку **Добавить**. При этом в решение добавляется файл **App.config**.

14. Скопируйте XML-код из приведенного выше примера в XML-файл. Сохраните файл.

15. Выполните сборку решения и скопируйте сборку и файл `App.config` в каталог *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\DataCollectors*.

16. Создайте параметры тестирования, использующие данный настраиваемый адаптер диагностических данных. Настройте параметры тестирования для сбора существующего файла.

     При выполнении тестов в Microsoft Test Manager эти параметры тестирования можно присвоить плану тестирования перед выполнением тестов или использовать команду "Запуск с параметрами" для присвоения или переопределения параметров тестирования. Дополнительные сведения о параметрах тестирования см. в статье [Сбор диагностических данных с помощью параметров тестирования](../test/collect-diagnostic-information-using-test-settings.md).

17. Запустите тесты с данными параметрами тестирования, выбрав свой адаптер диагностических данных.

     Указанный файл данных будет вложен в результаты теста при выполнении этого теста.

## <a name="see-also"></a>См. также

- [Практическое руководство. Создание адаптера диагностических данных](../test/how-to-create-a-diagnostic-data-adapter.md)
- [Практическое руководство. Создание специализированного редактора данных для адаптера диагностических данных](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)
- [Практическое руководство. Установка настраиваемого адаптера диагностических данных](../test/how-to-install-a-custom-diagnostic-data-adapter.md)
- [Создание адаптера диагностических данных для сбора пользовательских данных или воздействия на тестовый компьютер](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)