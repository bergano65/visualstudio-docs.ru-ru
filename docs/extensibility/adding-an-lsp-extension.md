---
title: Добавление расширения протокола языкового сервера (ru) Документы Майкрософт
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef2093915538f09f425fc961420c4a3078043c91
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740232"
---
# <a name="add-a-language-server-protocol-extension"></a>Добавление расширения протокола языкового сервера

Протокол языкового сервера (LSP) является общим протоколом, в виде JSON RPC v2.0, используемым для предоставления функций языковых услуг различным редакторам кода. Используя протокол, разработчики могут написать единый языковой сервер, чтобы предоставить функции языковых сервисов, таких как IntelliSense, диагностика ошибок, найти все ссылки и так далее, различным редакторам кода, поддерживающим LSP. Традиционно языковые сервисы в Visual Studio можно добавлять с помощью грамматических файлов TextMate для обеспечения основных функций, таких как выделение синтаксиса или написание пользовательских языковых сервисов, использующих полный набор AA-иномеров для получения более богатых данных. С поддержкой Visual Studio для LSP, есть третий вариант.

![Служба протокола языкового сервера в Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Протокол языкового сервера

![реализация протокола языкового сервера](media/lsp-implementation.png)

В этой статье описывается, как создать расширение Visual Studio, использующ языковой сервер на основе LSP. Он предполагает, что вы уже разработали LSP-языковой сервер и просто хотите интегрировать его в Visual Studio.

Для поддержки в Visual Studio языковые серверы могут общаться с клиентом (Visual Studio) через любой механизм передачи на основе потока, например:

* Стандартные потоки ввода/вывода
* Именованные каналы
* Розетки (только TCP)

Цель юрисовики и поддержки его в Visual Studio заключается в бортовых языковых услугах, которые не являются частью продукта Visual Studio. Он не предназначен для расширения существующих языковых услуг (например, C) в Visual Studio. Чтобы расширить существующие языки, обратитесь к руководству по расширению языковой службы (например, ["Roslyn" .NET Compiler Platform)](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)или [см.](../extensibility/extending-the-editor-and-language-services.md)

Для получения дополнительной информации о самом протоколе, смотрите документацию [здесь](https://github.com/Microsoft/language-server-protocol).

Для получения дополнительной информации о том, как создать сервер языка образца или как интегрировать существующий языковой сервер в Visual Studio Code, смотрите документацию [здесь](https://code.visualstudio.com/docs/extensions/example-language-server).

## <a name="language-server-protocol-supported-features"></a>Поддерживаемые функции Language Server Protocol

Следующие таблицы показывают, какие функции LSP поддерживаются в Visual Studio:

Сообщение | Имеет поддержку в визуальной студии
--- | ---
Инициализации | да
инициализирован | да
shutdown | да
exit | да
$/отменаЗапрос | да
окно/шоуСообщение | да
окно/шоуЗапросЗапрос | да
окно/logMessage | да
телеметрия/событие |
клиент/регистраторВозможност |
клиент/незарегистрированныйcapabilitи |
рабочее пространство/неизменениеконфигурации | да
рабочее пространство/didChangeWatchedFiles | да
рабочее пространство/символ | да
рабочее пространство/выполнениеКомандования | да
рабочее пространство/применениеEdit | да
textDocument/publishДиагностикы | да
textDocument/didOpen | да
textDocument/didChange | да
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | да
textDocument/didClose | да
textDocument/completion | да
завершение/разрешение | да
textDocument/hover | да
textDocument/signatureHelp | да
textDocument/references | да
textDocument/documentHighlight | да
textDocument/documentSymbol | да
textDocument/formatting | да
textDocument/rangeFormatting | да
textDocument/onTypeФорматирование |
textDocument/definition | да
textDocument/codeAction | да
textDocument/codeLens |
codeLens/resolve |
textDocument/documentLink |
documentLink/resolve |
textDocument/rename | да

## <a name="get-started"></a>Начало работы

> [!NOTE]
> Начиная с версии Visual Studio 2017 15.8, поддержка общего протокола Языкового сервера встроена в Visual Studio. Если вы создали расширения LSP с помощью предварительной версии [Language Server Client VSIX,](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) они перестанут работать, как только вы перейднетесь до версии 15.8 или выше. Вам нужно будет сделать следующее, чтобы получить lSP расширения снова работает:
>
> 1. Удалите Microsoft Visual Studio Языковой сервер Протокол Предварительный VSIX.
>
>    Начиная с версии 15.8, каждый раз, когда вы выполняете обновление в Visual Studio, предварительный просмотр VSIX автоматически обнаруживается и удаляется.
>
> 2. Обновите ссылку Nuget на последнюю непрепрепросмотрную версию для [пакетов LSP.](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)
>
> 3. Удалите зависимость от протокола Microsoft Visual Studio Language Server Protocol Preview VSIX в манифесте VSIX.
>
> 4. Убедитесь, что ваш VSIX определяет Visual Studio 2017 версия 15.8 Предварительный просмотр 3 в качестве нижней границы для установки цели.
>
> 5. заново собрать или повторно развернуть ресурс.

### <a name="create-a-vsix-project"></a>Создание проекта VSIX

Чтобы создать расширение языковой службы с помощью языкового сервера на основе LSP, сначала убедитесь, что у вас есть рабочая нагрузка разработки **расширения Visual Studio** для вашего экземпляра VS.

Далее, создайте новый проект VSIX, перепрыгивая в **файл** > **Новый проект** > **Visual C е** > **Расширяемость** > **VSIX проекта:**

![создать проект vsix](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>Языковой сервер и установка времени выполнения

По умолчанию расширения, созданные для поддержки языковых серверов на основе LSP в Visual Studio, не содержат самих языковых серверов или времени выполнения, необходимого для их выполнения. Разработчики расширения несут ответственность за распространение языковых серверов и необходимых времени выполнения. Есть несколько способов сделать это:

* Языковые серверы могут быть встроены в VSIX в качестве файлов содержимого.
* Создайте MSI для установки языкового сервера и/или необходимых времен выполнения.
* Предоставьте инструкции по Marketplace, информирующие пользователей о том, как получать время выполнения и языковые серверы.

### <a name="textmate-grammar-files"></a>Файлы грамматики TextMate

LSP не включает спецификацию о том, как обеспечить окрашивание текста для языков. Чтобы обеспечить пользовательскую окраску для языков в Visual Studio, разработчики расширений могут использовать файл грамматики TextMate. Чтобы добавить пользовательские textMate грамматики или тематические файлы, выполните следующие шаги:

1. Создайте папку под названием "Grammars" внутри расширения (или это может быть любое имя, которое вы выберете).

2. Внутри *папки Grammars,* включите любой * \*.tmlanguage*, * \*.plist*, * \*.tmtheme*, или * \*.json файлы,* которые вы хотели бы, чтобы обеспечить пользовательскую окраску.

   > [!TIP]
   > Файл *.tmtheme* определяет, как области отображают классификацию Visual Studio (названные цветными ключами). Для руководства, вы можете ссылаться на глобальный файл *.tmtheme* в *%ProgramFiles (x86)% -Microsoft Visual Studio\\\<версия>\\ \<SKU>»Common7-IDE-CommonExtensions Microsoft/TextMate/Starterkit-Themesg* каталог.

3. Создайте файл *.pkgdef* и добавьте строку, похожую на эту:

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

4. Нажмите справа на файлы и выберите **Свойства**. Измените действие **Build** на **содержимое** и **измените свойство «Включить» в** свойство VSIX на **истинное.**

После завершения предыдущих шагов папка Grammars добавляется в каталог *установки* пакета в качестве источника репозитория под названием «MyLang» («MyLang» — это просто название для дизамбигации и может быть любой уникальной строкой). Все грамматики *(.tmlanguage* файлы) и тематические файлы (*.tmtheme* файлы) в этом каталоге подобраны в качестве потенциалов, и они заменяют встроенные грамматики, предоставляемые TextMate. Если заявленные расширения грамматики соответствуют расширению открываемого файла, textMate вмешается.

## <a name="create-a-simple-language-client"></a>Создание простого языкового клиента

### <a name="main-interface---ilanguageclient"></a>Основной интерфейс - [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

После создания проекта VSIX добавьте следующий пакет NuGet (ы) в свой проект:

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> При зависимости от пакета NuGet после завершения предыдущих шагов в проект добавляются пакеты Newtonsoft.Json и StreamJsonRpc. **Не обновляйте эти пакеты, если вы не уверены, что эти новые версии будут установлены на версии Visual Studio, что ваше расширение цели.** Сборки не будут включены в ваш VSIX; вместо этого, они будут взяты из каталога установки Visual Studio. Если вы ссылаетесь на более новую версию сборок, чем то, что установлено на компьютере пользователя, ваше расширение не будет работать.

Затем можно создать новый класс, который реализует интерфейс [ILanguageClient,](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) который является основным интерфейсом, необходимым для языковых клиентов, подключенных к языковому серверу на основе LSP.

Ниже приведен пример:

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
            await StartAsync.InvokeAsync(this, EventArgs.Empty);
        }

        public Task OnServerInitializeFailedAsync(Exception e)
        {
            return Task.CompletedTask;
        }

        public Task OnServerInitializedAsync()
        {
            return Task.CompletedTask;
        }
    }
}
```

Основными методами, которые необходимо внедрить, являются [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) и [ActivateAsync.](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) вызывается, когда Visual Studio загрузила ваше расширение и ваш языковой сервер готов к началу. В этом методе можно немедленно вызвать делегата [StartAsync,](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) чтобы сигнализировать о том, что языковой сервер должен быть запущен, или сделать дополнительную логику и вызвать [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) позже. **Чтобы активировать языковой сервер, в какой-то момент необходимо позвонить в StartAsync.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) — это метод, который в конечном итоге вызывается, вызывая делегата [StartAsync.](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) Он содержит логику, чтобы запустить языковой сервер и установить подключение к нему. Объект соединения, содержащий потоки для записи на сервер и чтение с сервера, должен быть возвращен. Любые исключения, брошенные здесь, ловятся и отображаются пользователю через сообщение InfoBar в Visual Studio.

### <a name="activation"></a>Активация

Как только класс языкового клиента будет реализован, необходимо определить два атрибута, чтобы определить, как он будет загружен в Visual Studio и активирован:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio использует [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) для управления точками разъема. Атрибут [Экспорта](/dotnet/api/system.componentmodel.composition.exportattribute) указывает Visual Studio, что этот класс должен быть выбран в качестве точки расширения и загружен в соответствующее время.

Чтобы использовать MEF, необходимо также определить MEF как актив в манифесте VSIX.

Откройте свой разработчик манифеста VSIX и перейдите на вкладку **Активы:**

![добавить актив MEF](media/lsp-add-asset.png)

Нажмите **Новый** для создания нового актива:

![определить актив MEF](media/lsp-define-asset.png)

* **Тип**: Microsoft.VisualStudio.MefComponent
* **Источник**: Проект в текущем решении
* **Проект**: «Ваш проект»

### <a name="content-type-definition"></a>Определение типа содержимого

В настоящее время единственным способом загрузки расширения языкового сервера на основе LSP является тип содержимого файла. То есть при определении класса клиентского языка (который реализует [ILanguageClient),](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)необходимо определить типы файлов, которые при открытии при открывании загрузят ваше расширение. Если файлы, которые соответствуют определенному типу содержимого, не открываются, то ваше расширение не будет загружено.

Это делается путем `ContentTypeDefinition` определения одного или нескольких классов:

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

В предыдущем примере для файлов, заканчиваемых в расширении файла *.bar,* создается определение типа содержимого. Определение типа содержимого дается название "бар" и должно вытекать из [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017).

После добавления определения типа содержимого можно определить, когда загрузить расширение языкового клиента в классе языкового клиента:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

Добавление поддержки языковых серверов LSP не требует от вас реализации собственной проектной системы в Visual Studio. Клиенты могут открыть один файл или папку в Visual Studio, чтобы начать использовать свой языковой сервис. На самом деле, поддержка языковых серверов LSP предназначена для работы только в сценариях открытой папки/файлов. При реализации пользовательской проектной системы некоторые функции (например, настройки) не будут работать.

## <a name="advanced-features"></a>Дополнительные функции

### <a name="settings"></a>Параметры

Поддержка пользовательских настройках сервера для конкретного языка доступна, но она все еще находится в процессе совершенствования. Настройки специфичны для того, что поддерживает языковой сервер, и обычно контролируют, как языковой сервер излучает данные. Например, на языковом сервере может быть установлено максимальное количество сообщений об ошибках. Авторы расширения определят значение по умолчанию, которое может быть изменено пользователями для конкретных проектов.

Следуйте этим ниже, чтобы добавить поддержку настроек к расширению службы языков LSP:

1. Добавьте файл JSON (например, *MockLanguageExtensionSettings.json)* в проект, содержащий настройки и значения по умолчанию. Пример:

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. Нажмите на файл JSON и выберите **Свойства**. Измените действие **Build** на "Содержание" и "Включить в свойство VSIX до **истины.**

3. Реализация ConfigurationSections и возврат списка префиксов для параметров, определенных в файле JSON (В коде Visual Studio, это будет отображение к названию раздела конфигурации в package.json):

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. Добавьте файл .pkgdef в проект (добавьте новый текстовый файл и измените расширение файла на .pkgdef). Файл pkgdef должен содержать эту информацию:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    Образец.

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. Нажмите на файл .pkgdef и выберите **Свойства.** Измените действие **Build** на **содержимое** и включение в свойство **VSIX** на **истину.**

6. Откройте файл *source.extension.vsixmanifest* и добавьте актив во вкладку **Актив:**

   ![edit vspackage актив](media/lsp-add-vspackage-asset.png)

   * **Тип**: Microsoft.VisualStudio.VsPackage
   * **Источник**: Файл в файловой системе
   * **Путь**: «Путь к файлу *.pkgdef»*

### <a name="user-editing-of-settings-for-a-workspace"></a>Редактирование настройками для рабочего пространства пользователем

1. Пользователь открывает рабочее пространство, содержащее файлы, которыми владеет сервер.
2. Пользователь добавляет файл в папку *.vs* под названием *VSWorkspaceSettings.json.*
3. Пользователь добавляет строку в файл *VSWorkspaceSettings.json* для настройки, которую предоставляет сервер. Пример:

    ```json
    {
        "foo.maxNumberOfProblems": 10
    }
    ```

### <a name="enable-diagnostics-tracing"></a>Включить отслеживание диагностики

Отслеживание диагностики может быть включено для вывода всех сообщений между клиентом и сервером, что может быть полезно при отладке проблем. Для обеспечения отслеживания диагностики следует:

1. Откройте или создайте файл параметров рабочего пространства *VSWorkspaceSettings.json* (см. "Пользовательское редактирование настроек для рабочего пространства").
2. Добавьте следующую строку в файл езсона:

```json
{
    "foo.trace.server": "Off"
}
```

Существует три возможных значения для многословия следов:

* "Off": трассировка полностью выключена
* "Сообщения": отслеживание включено, но прослеживается только имя метода и идентификатор ответа.
* "Verbose": отслеживание включено; все сообщение rpc прослеживается.

При включении трассировки содержимое записывается в файл в каталоге *%temp% -VisualStudio-LSP.* В журнале следует формат именования *«LanguageClientNameName»-«Datetime Stamp».* В настоящее время отслеживание может быть включено только для сценариев открытых папок. Открытие одного файла для активации языкового сервера не имеет поддержки отслеживания диагностики.

### <a name="custom-messages"></a>Пользовательские сообщения

Существуют AI-аПО для облегчения передачи сообщений и получения сообщений с языкового сервера, которые не являются частью стандартного протокола Language Server Protocol. Для обработки пользовательских сообщений внедрить интерфейс [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) в классе языкового клиента. [Библиотека VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) используется для передачи пользовательских сообщений между вашим языковым клиентом и языковым сервером. Так как расширение lSP языкового клиента, как и любое другое расширение Visual Studio, вы можете добавить дополнительные функции (которые не поддерживаются LSP) в Visual Studio (с использованием других AI Visual Studio) в вашем расширении через пользовательские сообщения.

#### <a name="receive-custom-messages"></a>Получение пользовательских сообщений

Чтобы получать пользовательские сообщения с языкового сервера, реализуйте свойство [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017) на [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) и верните объект, который знает, как обрабатывать пользовательские сообщения. Пример ниже:

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

#### <a name="send-custom-messages"></a>Отправка пользовательских сообщений

Чтобы отправить пользовательские сообщения на языковой сервер, реализуйте метод [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) на [ILanguageClientCustomMessage.](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) Этот метод вызывается при запуска языкового сервера и готов к приему сообщений. Объект [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) передается в качестве параметра, который можно хранить для отправки сообщений на языковой сервер с помощью AIS [VS-StreamJsonRpc.](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) Пример ниже:

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

### <a name="middle-layer"></a>Средний слой

Иногда разработчик расширения может захотеть перехватить LSP-сообщения, отправленные и полученные с языкового сервера. Например, разработчик расширения может изменить параметр сообщения, отправленный для определенного сообщения LSP, или изменить результаты, возвращенные с языкового сервера для функции LSP (например, завершения). Когда это необходимо, разработчики расширения могут использовать API MiddleLayer для перехвата сообщений LSP.

Каждое сообщение LSP имеет свой собственный интерфейс среднего слоя для перехвата. Чтобы перехватить определенное сообщение, создайте класс, который реализует интерфейс среднего слоя для этого сообщения. Затем внедрите интерфейс [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) в классе клиентского языка и верните экземпляр объекта в свойстве [MiddleLayer.](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) Пример ниже:

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

Функция среднего слоя все еще находится в стадии разработки и еще не всеобъемлющая.

## <a name="sample-lsp-language-server-extension"></a>Пример расширения сервера LSP языка

Чтобы увидеть исходный код расширения образца с помощью API клиента LSP в Visual [LSP sample](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol)Studio, см.

## <a name="faq"></a>ВОПРОСЫ И ОТВЕТЫ

**Я хотел бы построить пользовательскую систему проектов в дополнение к моему языку LSP сервера, чтобы обеспечить более богатую поддержку функции в Visual Studio, как я могу это сделать?**

Поддержка языковых серверов на основе LSP в Visual Studio опирается на [функцию открытой папки](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/) и предназначена для того, чтобы не требовать пользовательской системы проекта. Вы можете создать свою собственную систему проектов, следуя инструкциям [здесь,](https://github.com/Microsoft/VSProjectSystem)но некоторые функции, такие как настройки, могут не работать. Логика инициализации по умолчанию для языковых серверов LSP заключается в том, чтобы пройти в корневой папке расположение папки, которая в настоящее время открыта, так что если вы используете пользовательскую систему проекта, возможно, потребуется предоставить пользовательскую логику во время инициализации, чтобы гарантировать, что ваш языковой сервер может начаться должным образом.

**Как добавить поддержку отладчика?**

Мы будем оказывать поддержку [общему протоколу отладки](https://code.visualstudio.com/docs/extensionAPI/api-debugging) в будущем выпуске.

**Если уже установлена языковая служба с поддержкой VS (например, JavaScript), могу ли я все еще установить расширение сервера LSP language server, которое предлагает дополнительные функции (например, linting)?**

Да, но не все функции будут работать должным образом. Конечная цель расширения сервера LSP-языка заключается в том, чтобы обеспечить языковые сервисы, не поддерживаемые Visual Studio. Вы можете создавать расширения, которые предлагают дополнительную поддержку с помощью языковых серверов LSP, но некоторые функции (например, IntelliSense) не будут гладкими. В целом рекомендуется использовать расширения сервера LSP-языкового сервера для предоставления новых языков, а не для расширения существующих.

**Где я могу опубликовать заполненный языковой сервер LSP VSIX?**

Смотрите инструкции Marketplace [здесь](walkthrough-publishing-a-visual-studio-extension.md).

## <a name="see-also"></a>См. также

- [Добавление поддержки редактора Visual Studio для других языков](../ide/adding-visual-studio-editor-support-for-other-languages.md)
