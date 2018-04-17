---
title: Добавление расширения протокола сервера языка | Документы Microsoft
ms.custom: ''
ms.date: 11/14/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bb6c82eab6878e99c9840ed593d9b9993056d391
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="adding-a-language-server-protocol-extension"></a>Добавление расширения языка протокола сервера

Язык сервера протокола (LSP) — общий протокол, в форме v2.0 JSON-RPC, используется для предоставления функциональных возможностей служб для различных редакторов кода языка. С помощью протокола, разработчики могут создавать сервер одного языка для обеспечения языка функции службы, такие как IntelliSense, диагностические сведения об ошибках, найти все ссылки, т. д., для различных редакторов кода, поддерживающие LSP. В большинстве случаев можно добавить языковые службы в Visual Studio, либо с помощью файлов грамматики TextMate для предоставления основные функциональные возможности, например выделение синтаксиса, или написав пользовательский языковой службы, с помощью полный набор API-интерфейсов расширения Visual Studio для предоставляют более подробные сведения. Теперь поддерживает LSP позволяет получить третий вариант.

![Служба протокола языка сервера в Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Язык протокола сервера

Дополнительные сведения о сам протокол см. в документации [здесь](https://github.com/Microsoft/language-server-protocol). Visual Studio реализация языка сервера протокола находится в предварительной версии и поддержки считается экспериментальный. В предварительной версии — в виде расширения ([предварительной версией клиента языка сервера протокола](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)), **, но это расширение можно установить только на просмотр канала в Visual Studio**. Более поздний выпуск Visual Studio будет включает встроенную поддержку протокола языка сервера, в какое время будут удалены флаг предварительного просмотра. **Предварительный просмотр не следует использовать в рабочей среде.**

Дополнительные сведения о том, как создать модель языка сервера или как интегрировать существующий сервер языка в код Visual Studio, см. в документации [здесь](https://code.visualstudio.com/docs/extensions/example-language-server).

![Реализация протокола сервера языка](media/lsp-implementation.png)

В этой статье описывается создание расширения Visual Studio, которая использует язык на основе LSP сервер. Предполагается, что сервер язык на основе LSP уже разработали и просто хотите интегрировать в Visual Studio.

Для получения поддержки в Visual Studio языка серверы могут взаимодействовать с клиентом (Visual Studio) посредством следующих механизмов:

* Стандартных потоков ввода вывода
* Именованные каналы
* сокеты

LSP и для него поддержку в Visual Studio призван встроенного языковой службы, которые не являются частью продукта Visual Studio. Он не предназначен для расширения существующих служб языка (например, C#) в Visual Studio. Для расширения существующих языков, см. руководство по службе языка расширения (например, [платформой компилятора .NET «Roslyn»](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)).

## <a name="language-server-protocol-features-supported"></a>Поддерживаемые возможности протокола сервера языка

В Visual Studio до сих поддерживаются следующие функции LSP:

Сообщение | Поддерживает работу в Visual Studio
--- | ---
Инициализация | да
инициализирован | да
завершение работы | да
Выход | да
$/ cancelRequest | да
окна/showMessage | да
окна/showMessageRequest | да
окна/logMessage | да
Данные телеметрии и события |
Клиент или registerCapability |
Клиент или unregisterCapability |
Рабочая область/didChangeConfiguration | да
Рабочая область/didChangeWatchedFiles | да
Рабочая область символ | да
Рабочая область/executeCommand | да
Рабочая область/applyEdit | да
textDocument/publishDiagnostics | да
textDocument/didOpen | да
textDocument/didChange | да
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | да
textDocument/didClose | да
textDocument/завершения | да
Завершение и разрешения | да
textDocument или при наведении курсора мыши | да
textDocument/signatureHelp | да
textDocument и ссылки | да
textDocument/documentHighlight |
textDocument/documentSymbol | да
textDocument и форматирование | да
textDocument/rangeFormatting | да
textDocument/onTypeFormatting |
textDocument или определение | да
textDocument/codeAction | да
textDocument/codeLens |
codeLens и разрешения |
textDocument/documentLink |
documentLink и разрешения |
textDocument или переименуйте | да

## <a name="getting-started"></a>Начало работы

### <a name="create-a-vsix-project"></a>Создайте проект VSIX

Чтобы создать расширение языковой службы, с помощью сервера язык на основе LSP, сначала убедитесь, что у вас есть **разработки расширения Visual Studio** установки для экземпляра VS рабочей нагрузки.

Затем создать новый пустой VSIXProject, перейдя к **файл** > **новый проект** > **Visual C#**  >   **Расширяемость** > **проект VSIX**:

![Создайте проект vsix](media/lsp-vsix-project.png)

Для предварительной версии VS поддержка LSP будет в формате VSIX ([Microsoft.VisualStudio.LanguageServer.Client.Preview](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)). Расширения разработчиков, которые хотите создать расширение с помощью серверов LSP языка должны зависеть от этот VSIX-ФАЙЛ. Таким образом, клиентам, которым требуется установить это расширение языка сервера **необходимо сначала установить VSIX Предварительный просмотр языка сервера протокола клиента.**

Для определения зависимостей VSIX, откройте конструктор манифеста VSIX для вашего VSIX (, дважды щелкнув файл source.extension.vsixmanifest в проекте) и перейдите к **зависимости**:

![Добавьте ссылку на язык сервера протокола клиента](media/lsp-reference-lsp-dependency.png)

Создание новой зависимости следующим образом:

![Определение языка сервера протокола клиента зависимостей](media/lsp-define-lsp-dependency.png)

* **Источник**: определяются вручную
* **Имя**: предварительной версией клиента языка сервера протокола
* **Идентификатор**: Microsoft.VisualStudio.LanguageServer.Client.Preview
* **Диапазон версий**: [1.0,2.0)
* **Как обеспечивается разрешения зависимости**: установлено пользователем
* **Загрузить URL-адрес**: [https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)

> [!NOTE]
> **URL-адрес загрузки** должно быть заполнено, чтобы пользователи, устанавливающие расширения знали, как установить необходимую зависимость.

### <a name="language-server-and-runtime-installation"></a>Установка сервера и среды выполнения языка

По умолчанию модули, созданные для поддержки языка на основе LSP серверов в Visual Studio не будет содержать самих серверов языка и среды выполнения, необходимые для их выполнения. Разработчикам расширений отвечают за распределение серверов языка и необходимости среды выполнения. Чтобы сделать это несколькими способами:

* Серверы языка может быть внедрен в VSIX как файлы содержимого.
* Создание MSI-ФАЙЛ для установки языка сервера или необходимости среды выполнения.
* Приведены инструкции о пользователей Marketplace получении серверов сред выполнения и языка.

### <a name="textmate-grammar-files"></a>Файлы TextMate грамматики

LSP не содержит спецификацию указания выделение цветом текста для языков. Чтобы предоставить пользовательские окраски для языков в Visual Studio, разработчикам расширений можно использовать файл грамматики TextMate. Чтобы добавить пользовательские файлы грамматики или темы TextMate, выполните следующие действия.

1. Создайте папку с именем «Грамматик» внутри модуля или он может быть любое имя.

2. В папке «Грамматик» включают *.tmlanguage, *.plist, *.tmtheme или файлы *.json, которой вы хотите предоставляющих настраиваемые выделение цветом.

3. Щелкните правой кнопкой мыши на файлы, а также выберите **свойства**. Изменить действие при построении **содержимого** и **включить в VSIX** значение true.

4. Создание pkgdef-файл и добавьте строку следующего вида:

  ```xml
  [$RootKey$\TextMate\Repositories]
  "MyLang"="$PackageFolder$\Grammars"
  ```

5. Щелкните правой кнопкой мыши на файлы, а также выберите **свойства**. Изменить действие при построении **содержимого** и **включить в VSIX** значение true.

После завершения предыдущих шагов, будет добавлена папка «Грамматик» Установка пакета каталоге, что и исходный репозиторий с именем «MyLang» («MyLang» только имя для устранения неоднозначности, может быть любая уникальная строка). Все грамматики (.tmlanguage-файлы) и тему (файлы .tmtheme) в этом каталоге, если выбраны как используемых, они имеют приоритет встроенных грамматик, в состав TextMate. Если файл грамматики объявленный расширения соответствует расширению открытого файла, TextMate будет шаг.

## <a name="creating-a-simple-language-client"></a>Создание простой язык клиента

### <a name="main-interface---ilanguageclientdotnetapimicrosoftvisualstudiolanguageserverclientilanguageclientviewvisualstudiosdk-2017"></a>Основной интерфейс - [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

После создания проекта VSIX, добавьте следующие пакеты NuGet в проект:

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> При принимает зависимость от пакета NuGet после выполнения предыдущих шагов, пакеты Newtonsoft.Json и StreamJsonRpc добавляются в проект. **Эти пакеты не обновляются, если вы уверены, что эти новые версии будут установлены в версии Visual Studio, используемой для расширения**. Сборки не будут включены в ваш VSIX--вместо этого они извлекаются из каталога установки Visual Studio. Если вы ссылаетесь более новой версии сборки, чем установленных на компьютере пользователя, расширение *не будет работать*.

Затем можно создать новый класс, реализующий [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) интерфейса, основной интерфейс, необходимый для подключения к серверу язык на основе LSP клиентов языка.

Ниже приведен пример.

```csharp
namespace MockLanguageExtension
{
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
        public string Name => "Bar Language Extension";

        public IEnumerable<string> ConfigurationSections => null;

        public object InitializationOptions => null;

        public IEnumerable<string> FilesToWatch => null;

        public event AsyncEventHandler<EventArgs> StartAsync;
        public event AsyncEventHandler<EventArgs> StopAsync;

        public async Task<Connection> ActivateAsync(CancellationToken token)
        {
            await Task.Yield();

            ProcessStartInfo info = new ProcessStartInfo();
            info.FileName = Path.Combine(Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location), "Server", @"MockLanguageServer.exe");
            info.Arguments = "bar";
            info.RedirectStandardInput = true;
            info.RedirectStandardOutput = true;
            info.UseShellExecute = false;
            info.CreateNoWindow = true;

            Process process = new Process();
            process.StartInfo = info;

            if (process.Start())
            {
                return new Connection(process.StandardOutput.BaseStream, process.StandardInput.BaseStream);
            }

            return null;
        }

        public async Task OnLoadedAsync()
        {
            await StartAsync?.InvokeAsync(this, EventArgs.Empty);
        }

        public async Task OnServerInitializeFailedAsync(Exception e)
        {
            return Task.CompletedTask;
        }

        public async Task OnServerInitializedAsync()
        {
            return Task.CompletedTask;
        }
    }
}
```

Основные методы, которые должны быть реализованы [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) и [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017). [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) вызывается при загрузке расширения Visual Studio и Готово к запуску язык сервера. В этот метод можно вызвать [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) делегат немедленно указывают сервер языка должен быть запущен, или можно выполнить дополнительную логику и вызвать [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) позже. **Чтобы активировать сервер язык, необходимо вызвать StartAsync в определенный момент.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) метод в конечном счете вызывается путем вызова [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) делегата; он содержит логику для запуска языка сервера и установить подключение к нему. Объект соединения, содержащий потоков для чтения с сервера и записи на сервере должен быть возвращен. Все исключения перехватываются и отображается для пользователя с помощью сообщение информационную панель в Visual Studio.

### <a name="activation"></a>Активация

После реализации языка клиентском классе, необходимо иметь для определения двух атрибутов для того, чтобы определить, как его будут загружены в Visual Studio и активации:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio использует [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) для управления точки расширения. [Экспорт](https://msdn.microsoft.com/library/system.componentmodel.composition.exportattribute(v=vs.110).aspx) атрибут указывает Visual Studio, что используются как точку расширения этот класс и они будут загружены в соответствующее время.

Чтобы использовать MEF, необходимо также определить MEF как ресурс в манифесте VSIX.

Откройте конструктор манифеста VSIX и перейдите к **активы** вкладки:

![Добавление средств MEF](media/lsp-add-asset.png)

Щелкните "Создать" для создания нового средства:

![Определение активов MEF](media/lsp-define-asset.png)

* **Тип**: Microsoft.VisualStudio.MefComponent
* **Источник**: проект в текущем решении
* **Проект**: [проект]

### <a name="content-type-definition"></a>Определение типа содержимого

В настоящее время единственным способом, чтобы загрузить расширение серверного ваш язык на основе LSP является тип содержимого файла. То есть при определении клиентском классе языка (, реализующий [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)), необходимо определить типы файлов, когда открыт, приводит к созданию расширения для загрузки. Если нет файлов, которые соответствуют вашей определенный тип содержимого открываются, решение не будет загружено.

Это осуществляется посредством определения одного или нескольких классов ContentTypeDefinition:

```csharp
namespace MockLanguageExtension
{
    public class BarContentDefinition
    {
        [Export]
        [Name("bar")]
        [BaseDefinition(CodeRemoteContentDefinition.CodeRemoteContentTypeName)]
        internal static ContentTypeDefinition BarContentTypeDefinition;


        [Export]
        [FileExtension(".bar")]
        [ContentType("bar")]
        internal static FileExtensionToContentTypeDefinition BarFileExtensionDefinition;
    }
}
```

В предыдущем примере создается определение типа содержимого для файлов, которые заканчиваются на `.bar` расширение имени файла. Определение типа содержимого присваивается имя «панель» и **должен** являются производными от [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017).

После добавления определения типа содержимого, можно определить причины для загрузки расширения языка клиента в классе клиента языка:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

Добавление поддержки для языка серверов LSP не требуется реализовывать собственную систему проектов в Visual Studio. Клиентам можно открыть один файл или папку в Visual Studio, чтобы приступить к использованию службы языка. На самом деле поддержка серверов языка LSP предназначен для работы только в сценариях, открыть папку или файл. Если реализована в системе пользовательских проектов, некоторые функции (например, параметры), не будут работать.

## <a name="advanced-features"></a>Дополнительные возможности

### <a name="settings"></a>Параметры

Поддержка настраиваемые параметры языка сервера доступна для предварительной версии LSP поддержки в Visual Studio, но выполняется по-прежнему которое совершенствуется. Настройки, специфичные для что языка сервер поддерживает и обычно управлять как сервер языка передает данные. Например язык сервера могут быть параметр максимального числа ошибок. Авторы расширения может определить значение по умолчанию, который может быть изменен пользователями для конкретных проектов.

Выполните эти шаги, чтобы добавить поддержку для параметров модуля LSP языковой службы.

1. Добавьте файл JSON (например, «MockLanguageExtensionSettings.json») в проекте, который содержит параметры и их значения по умолчанию. Пример:

  ```json
  {
    "foo.maxNumberOfProblems": -1
  }
  ```
2. Щелкните правой кнопкой мыши файл JSON и выберите **свойства**. Изменение **построения** действие «Content» и «включить в VSIX "значение true.

3. Реализация ConfigurationSections и возвращают список префиксов для параметров, определенных в файле JSON (в коде Visual Studio, это будут сопоставлены имя раздела конфигурации в package.json):

  ```csharp
  public IEnumerable<string> ConfigurationSections
  {
      get
      {
          yield return "foo";
      }
  }
  ```
4. Добавьте файл pkgdef в проект (добавьте новый текстовый файл и измените расширение файла на .pkgdef). Pkgdef-файла должна содержать следующие сведения:

  ```xml
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
  ```

5. Щелкните правой кнопкой мыши pkgdef-файл и выберите **свойства**. Изменение **построения** действия «Content» и «Включить в VSIX» равным true.

6. Откройте `source.extension.vsixmanifest` и добавьте ресурс в **активов** вкладки:

  ![изменить активов vspackage](media/lsp-add-vspackage-asset.png)

  * **Тип**: Microsoft.VisualStudio.VsPackage
  * **Источник**: файл в файловой системе
  * **Путь**: [путь к pkgdef-файла]

### <a name="user-editing-of-settings-for-a-workspace"></a>Изменение параметров для рабочей области пользователя

1. Пользователь открывает рабочую область, содержащую файлы, которыми владеет сервера.
2. Пользователь добавляет файл в папку «удаляйте» с именем «VSWorkspaceSettings.json».
3. Пользователь добавляет строку в файле VSWorkspaceSettings.json параметр, который предоставляет этот сервер. Пример:

  ```json
  {
    "foo.maxNumberOfProblems": 10
  }
  ```
### <a name="enabling-diagnostics-tracing"></a>Включение трассировки диагностики
Можно включить трассировку диагностики для вывода всех сообщений между клиентом и сервером, которые могут быть полезны при отладке проблем.  Чтобы включить диагностическую трассировку, выполните следующие действия.

1. Откройте или создайте файл параметров рабочей области «VSWorkspaceSettings.json» (см. «Пользователь редактирует параметров для рабочей области»).
2. Добавьте следующую строку в файле параметров json:

```json
{
    "foo.server.trace": "Off"
}
```

Существует три возможных значения для детализации трассировки:
* «Off»: полностью отключить трассировку
* «Сообщения»: трассировка включена, но метод только имя и ответа идентификатор трассируются.
* «Verbose»: трассировка включена; Это событие регистрируется сообщение целиком rpc.

При включении трассировки на содержимое записывается в файл в каталоге «% temp%\VisualStudio\LSP».  Журнал формат именования `[LanguageClientName]-[Datetime Stamp].log`.  В настоящее время трассировку можно включить только для сценариев, открыть папку.  Открытия одного файла для активации сервера языка отсутствует поддержка трассировки диагностики.

### <a name="custom-messages"></a>Пользовательские сообщения

Существует API-интерфейсов на месте для упрощения передачи сообщений и прием сообщений от языка сервера, которые не являются частью стандартного языка протокол сервера. Для обработки пользовательских сообщений, реализовать [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) интерфейса в клиентском классе языка. [VS StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) библиотека используется для передачи пользовательских сообщений между клиентом языка и языка сервера. Так как расширение языка клиента LSP так же, как любое другое расширение Visual Studio, можно добавить дополнительные функции (которые не поддерживаются LSP) для Visual Studio (с использованием других API-интерфейсы Visual Studio) расширения с помощью пользовательских сообщений.

#### <a name="receiving-custom-messages"></a>Получение пользовательских сообщений

Чтобы получить пользовательские сообщения от языка сервера, реализовать [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017) свойство [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) и вернуть объект, который знает, как обрабатывать пользовательские сообщения . Пример ниже.

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public object CustomMessageTarget
    {
        get;
        set;
    }

    public class CustomTarget
    {
        public void OnCustomNotification(JToken arg)
        {
            // Provide logic on what happens OnCustomNotification is called from the language server
        }

        public string OnCustomRequest(string test)
        {
            // Provide logic on what happens OnCustomRequest is called from the language server
        }
    }
}
```

#### <a name="sending-custom-messages"></a>Отправка пользовательских сообщений

Для отправки на сервер языка пользовательские сообщения, реализуйте [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) метод [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017). Этот метод вызывается, когда сервер языка не запущен и готов к приему сообщений. Объект [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) объект передается как параметр, который затем можно сохранить для отправки сообщений для языка сервера с помощью [VS StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) API-интерфейсы. Пример ниже.

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public async Task AttachForCustomMessageAsync(JsonRpc rpc)
    {
        await Task.Yield();

        this.customMessageRpc = rpc;
    }

    public async Task SendServerCustomNotification(object arg)
    {
        await this.customMessageRpc.NotifyWithParameterObjectAsync("OnCustomNotification", arg);
    }

    public async Task<string> SendServerCustomMessage(string test)
    {
        return await this.customMessageRpc.InvokeAsync<string>("OnCustomRequest", test);
    }
}
```

### <a name="middle-layer"></a>Средний уровень

Иногда разработчик расширения может потребоваться перехвата LSP сообщений, отправленных и полученных от языка сервера. Например разработчик расширения могут для изменения параметра сообщения, отправленные для определенного сообщения LSP или изменять результаты, возвращаемые с сервера языка LSP возможности (например, варианты завершения). При необходимости это расширение разработчики могут использовать MiddleLayer API для перехвата сообщений LSP.

Каждое сообщение LSP имеет свой собственный интерфейс среднего уровня для перехвата. Для перехвата определенного сообщения, создайте класс, реализующий интерфейс среднего уровня для сообщения. Затем реализовать [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) в клиентском классе язык интерфейса и возвращает экземпляр объекта в [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) свойство. Пример ниже.

```csharp
public class MockLanguageClient: ILanguageClient, ILanguageClientCustomMessage
{
    public object MiddleLayer => MiddleLayerProvider.Instance;

    private class MiddleLayerProvider : ILanguageClientWorkspaceSymbolProvider
    {
        internal readonly static MiddleLayerProvider Instance = new MiddleLayerProvider();

        private MiddleLayerProvider()
        {
        }

        public async Task<SymbolInformation[]> RequestWorkspaceSymbols(WorkspaceSymbolParams param, Func<WorkspaceSymbolParams, Task<SymbolInformation[]>> sendRequest)
        {
            // Send along the request as given
            SymbolInformation[] symbols = await sendRequest(param);

            // Only return symbols that are "files"
            return symbols.Where(sym => string.Equals(new Uri(sym.Location.Uri).Scheme, "file", StringComparison.OrdinalIgnoreCase)).ToArray();
        }
    }
}
```

Компонент среднего уровня, находится в разработке и еще не полный.

## <a name="sample-lsp-language-server-extension"></a>Пример LSP языка сервер расширения

Чтобы просмотреть исходный код образца модуля, с помощью API клиента LSP в Visual Studio, см. Примеры VSSDK-расширения [LSP образец](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol).

## <a name="faq"></a>часто задаваемые вопросы

**Как для создания пользовательского проекта системы в качестве дополнения серверу LSP языка для обеспечения более широкую поддержку компонентов в Visual Studio как go о это сделать?**

Поддержка языка на основе LSP серверов в Visual Studio зависит от [возможность открыть папку](https://blogs.msdn.microsoft.com/visualstudio/2016/04/12/open-any-folder-with-visual-studio-15-preview/) и предназначенный специально для требует системе пользовательских проектов. Можно создавать собственные системе пользовательских проектов, следуя инструкциям [здесь](https://github.com/Microsoft/VSProjectSystem), но некоторые функции, такие как параметры, может не работать. Логику инициализации по умолчанию для серверов LSP языка является передача в расположение корневой папки, папки открытых в данный момент, поэтому при использовании системе пользовательских проектов, может потребоваться для предоставления пользовательской логики во время инициализации, чтобы вы можете языка сервера загрузиться надлежащим образом.

**Добавление поддержки отладчика**

Мы предоставим поддержка [общую отладочную протокола](https://code.visualstudio.com/docs/extensionAPI/api-debugging) в будущем выпуске.

**Если уже VS поддерживаемого языка установлена служба (например, JavaScript), можно по-прежнему установить расширение языка сервера LSP, предлагает дополнительные возможности (например, linting)?**

Да, но не все компоненты будут работать неправильно. Ultimate LSP языка серверных расширений предназначена для включения служб языка, изначально не поддерживаемого средой Visual Studio. Можно создать расширения, которые обеспечивают дополнительную поддержку, с помощью серверов LSP языка, но некоторые функции (например, технология IntelliSense) не будет удобства. В общем случае рекомендуется использования серверных расширений языка LSP для предоставления новых функций языка, не расширение уже существующих.

**Где опубликовать серверу языка завершенного LSP VSIX?**

См. инструкции Marketplace [здесь](walkthrough-publishing-a-visual-studio-extension.md).
