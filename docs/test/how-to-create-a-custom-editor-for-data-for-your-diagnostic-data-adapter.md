---
title: Создание специализированного редактора данных для адаптера диагностических данных в Visual Studio | Документы Майкрософт
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- Diagnostic Data Adapter, creating custom editor
ms.assetid: 24970227-d1ea-4f6d-9839-e911478848ba
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: d1426d6e51ac132ee766913e69827df1d9558fba
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter"></a>Практическое руководство. Создание специализированного редактора данных для адаптера диагностических данных

При создании адаптера диагностических данных может быть нужно дать пользователю возможность настраивать определенные данные при выборе специализированного адаптера диагностических данных в параметрах тестирования. Например, можно выбирать данные конфигурации, указывающие, какие разделы реестра следует извлекать, какой уровень сетевой нагрузки нужно моделировать или в каком каталоге находятся присоединяемые временные или рабочие файлы.

Для установки начальных значений адаптера диагностических данных необходимо использовать файл конфигурации. Чтобы пользователь мог изменять данные конфигурации, можно предоставить ему специализированный редактор.

Для создания собственного редактора нужно создать пользовательский элемент управления, реализующий интерфейс <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor>.

Для задания класса редактора, используемого для редактирования параметров конфигурации диагностических данных, в адаптере диагностических данных может использоваться атрибут <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>.

Также нужно указать данные конфигурации по умолчанию, которые следует использовать.  См. [Пример проекта для создания адаптера диагностических данных](../test/sample-project-for-creating-a-diagnostic-data-adapter.md) для примера конфигурации по умолчанию.

Выполните следующие действия, чтобы создать специализированный редактор, обновляющий данные параметров тестирования при использовании специализированного адаптера диагностических данных.

> [!NOTE]
> Для создания специализированного редактора необходимо сначала создать адаптер диагностических данных с примененным к классу атрибутом <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>. Можно дополнительно включить в атрибут свойство <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute.HelpUri*>, чтобы указать источник содержимого справки для этого редактора. Дополнительные сведения о создании адаптера диагностических данных см. в разделе [Практическое руководство. Создание адаптера диагностических данных](../test/how-to-create-a-diagnostic-data-adapter.md).

Полный пример проекта адаптера диагностических данных, включая специализированный редактор конфигурации, см. в разделе [Пример проекта для создания адаптера диагностических данных](../test/sample-project-for-creating-a-diagnostic-data-adapter.md).

## <a name="to-create-a-custom-editor-for-your-diagnostic-data-adapter"></a>Для создания специализированного редактора для адаптера диагностических данных выполните следующие действия.

1.  Создайте пользовательский элемент управления в проекте для адаптера диагностических данных. Это делается следующим образом.

    1.  Щелкните правой кнопкой мыши проект кода, содержащий класс адаптера диагностических данных, и последовательно выберите **Добавить** и **Пользовательский элемент управления**.

    2.  Для данного примера добавьте в форму метку с текстом **Имя файла данных:** и текстовое поле с именем **FileTextBox**, позволяющее пользователям вводить необходимые данные.

    > [!NOTE]
    > В настоящее время поддерживаются только пользовательские элементы управления Windows Forms.

2.  Добавьте в раздел объявлений следующие строки кода.

    ```csharp
    using System.Xml;
    using Microsoft.VisualStudio.TestTools.Common;
    using Microsoft.VisualStudio.TestTools.Execution;
    ```

3.  Преобразуйте данный пользовательский элемент управления в специализированный редактор.

    1.  Щелкните правой кнопкой мыши пользовательский элемент управления в проекте кода и выберите команду **Просмотреть код**.

    2.  Настройте реализацию классом интерфейса редактора <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor> следующим образом.

    ```csharp
    public partial class MyDataConfigEditor :
         UserControl, IDataCollectorConfigurationEditor
    ```

    1.  Щелкните правой кнопкой мыши <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor> в коде и выберите команду **Реализовать интерфейс**. Методы, которые необходимо реализовать для данного интерфейса, добавляются в класс.

    2.  Добавьте объект <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> в пользовательский элемент управления для редактора, чтобы он определялся как редактор адаптера диагностических данных, заменив поля **Организация**, **Продукт** и **Версия** соответствующими сведениями об адаптере диагностических данных:

        ```csharp
        [DataCollectorConfigurationEditorTypeUri(
            "configurationeditor://MyCompany/MyConfigEditor/1.0")]
        ```

4.  Добавьте две закрытых переменных, как показано ниже.

    ```csharp
    private DataCollectorSettings collectorSettings;
    private IServiceProvider ServiceProvider { get; set; }
    ```

5.  Добавьте код для инициализации редактора для адаптера диагностических данных. Используя данные в переменной settings, в поля пользовательского элемента управления можно добавлять значения по умолчанию. Это данные, находящиеся в элементе `<DefaultConfiguration>` в XML-файле конфигурации адаптера.

    ```csharp
    public void Initialize(
        IServiceProvider svcProvider,
        DataCollectorSettings settings)
    {
        ServiceProvider = svcProvider;
        collectorSettings = settings;

        // Display the default file name as listed in the settings file.
        this.SuspendLayout();
        this.FileTextBox.Text = getText(collectorSettings.Configuration);
        this.ResumeLayout();
    }
    ```

6.  Добавьте следующий код для сохранения данных из элементов управления редактора в формате XML, который использует API адаптера диагностических данных:

    ```csharp
    public DataCollectorSettings SaveData()
    {
        collectorSettings.Configuration.InnerXml =
            String.Format(
    @"<MyCollectorName
        xmlns=""http://MyCompany/schemas/MyDiagnosticDataCollector/1.0"">
      <File FullPath=""{0}"" />
    </MyCollectorName>",
        FileTextBox.Text);
        return collectorSettings;
    }
    ```

7.  Если это важно, добавьте код проверки правильности данных в метод `VerifyData` или назначьте для этого метода возврат значения `true`.

    ```csharp
    public bool VerifyData()
    {
        // Not currently verifying data
        return true;
    }
    ```

8.  (Необязательно) Можно добавить в метод `ResetToAgentDefaults()`, использующий закрытый метод `getText()`, код сброса данных на начальные значения, содержащиеся в XML-файле конфигурации.

    ```csharp
    // Reset to default value from XML configuration
    // using a custom getText() method
    public void ResetToAgentDefaults()
    {
        this.FileTextBox.Text = getText(collectorSettings.DefaultConfiguration);
    }

    // Local method to read the configuration settings
    private string getText(XmlElement element)
    {
        // Setup namespace manager with our namespace
        XmlNamespaceManager nsmgr =
            new XmlNamespaceManager(
                element.OwnerDocument.NameTable);

        // Find all the "File" elements under our configuration
        XmlNodeList files = element.SelectNodes("//ns:MyCollectorName/ns:File", nsmgr);

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
    ```

9. Выполните построение решения. Скопируйте сборку адаптера диагностических данных и XML-файл конфигурации (`<diagnostic data adapter name>.dll.config`) в следующее расположение (в зависимости от каталога установки): *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\DataCollectors*.

    > [!NOTE]
    > Хотя редактор конфигурации может находиться в проекте и сборке, отличных от проекта и сборки адаптера диагностических данных, они могут также находиться в одной сборке.

10. Чтобы использовать адаптер диагностических данных при тестировании, нужно выбрать его в списке существующих параметров тестирования или создать новый с помощью Microsoft Test Manager или Visual Studio, а затем выбрать свой адаптер диагностических данных.

     Адаптер отображается на вкладке **Данные и диагностика** параметров тестирования и имеет понятное имя, присвоенное классу.

11. Чтобы настроить адаптер диагностических данных для параметров тестирования, нажмите кнопку **Настройка** рядом с именем адаптера.

     Откроется специализированный редактор.

12. При необходимости измените поля в пользовательском редакторе и нажмите кнопку **Сохранить**.

13. При выполнении тестов в Microsoft Test Manager эти параметры тестирования можно присвоить плану тестирования перед выполнением тестов или использовать команду **Запуск с параметрами** для присвоения или переопределения параметров тестирования. Дополнительные сведения о параметрах тестирования см. в статье [Сбор диагностических данных с помощью параметров тестирования](../test/collect-diagnostic-information-using-test-settings.md).

14. Чтобы можно было использовать новый редактор конфигурации с адаптером диагностических данных, необходимо применить атрибут <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> к каждому классу адаптер диагностических данных, который должен использовать этот редактор, а затем перекомпилировать и установить его на клиентский компьютер. Дополнительные сведения об установке адаптеров диагностических данных и редакторов конфигурации см. в разделе [Практическое руководство. Установка настраиваемого адаптера диагностических данных](../test/how-to-install-a-custom-diagnostic-data-adapter.md).

15. Выполните тесты с данными параметрами тестирования, выбрав свой адаптер диагностических данных.

     Файл данных, указанный в редакторе, присоединяется к результатам тестов.

 Дополнительные сведения о том, как настраивать параметры тестирования для использования среды при выполнении тестов, см. в разделе [Сбор данных диагностики в ручных тестах (VSTS)](/vsts/manual-test/collect-diagnostic-data) или [Сбор диагностических данных во время тестирования (VSTS)](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests).

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.TestTools.Execution.IDataCollectorConfigurationEditor>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- [Создание адаптера диагностических данных для сбора пользовательских данных или воздействия на тестовый компьютер](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)
- [Сбор диагностических данных с помощью параметров тестирования](../test/collect-diagnostic-information-using-test-settings.md)
- [Пример проекта для создания адаптера диагностических данных](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)