---
title: Добавление расширения протокола языкового сервера | Документация Майкрософт
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
ms.openlocfilehash: 9539fdb1a349fe7fc7331e8d3f352506eac9d00b
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081687"
---
# <a name="add-a-language-server-protocol-extension"></a>Добавление расширения протокола языкового сервера

Протокол Server языка (LSP) — это общий протокол, в виде версии 2.0 JSON RPC, используемый для предоставления функций службы для различных редакторов кода языка. С помощью протокола, разработчики могут создавать сервер для одного языка на предоставление языка функции службы, таких как IntelliSense, диагностические сведения об ошибках, найти все ссылки, т. д., для различных редакторов кода, которые поддерживают LSP. В большинстве случаев можно добавить языковые службы в Visual Studio, либо с помощью файлов грамматики TextMate для предоставления базовых функциональных возможностей, таких как выделение синтаксиса, или написав пользовательские языковые службы, используя полный набор интерфейсов API расширяемости Visual Studio для предоставляют более подробные данные. Теперь поддержка LSP предлагает третий вариант.

![языковая служба протокола сервера в Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Протокол языкового сервера

![Реализация протокола server языка](media/lsp-implementation.png)

В этой статье описывается, как создать расширение Visual Studio, которая использует сервер язык на основе LSP. Предполагается, что вы уже разработали серверу язык на основе LSP и просто хотите его интеграция с Visual Studio.

Для получения поддержки в Visual Studio, язык серверы могут взаимодействовать с клиентом (Visual Studio) с помощью любого механизма передачи потока, используя, например:

* Стандартных потоков ввода вывода
* Именованные каналы
* Сокеты (TCP)

Цель LSP и его поддержку в Visual Studio — встроенные языковые службы, которые не являются частью продукта Visual Studio. Он не предназначен для расширения существующих служб языка (например, C#) в Visual Studio. Чтобы расширить существующие языки, см. руководство по расширяемости языковой службы (например, [платформы компилятора .NET «Roslyn»](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)).

Дополнительные сведения о самом протоколе см. в документации [здесь](https://github.com/Microsoft/language-server-protocol).

Дополнительные сведения о том, как создать пример языка сервера или как интегрировать существующий сервер языка в Visual Studio Code см. в документации [здесь](https://code.visualstudio.com/docs/extensions/example-language-server).

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
Данные телеметрии и событий |
Клиент/registerCapability |
Клиент/unregisterCapability |
Рабочая область/didChangeConfiguration | да
Рабочая область/didChangeWatchedFiles | да
Рабочая область, символа | да
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
Завершение или исправить | да
textDocument/при наведении курсора мыши | да
textDocument/signatureHelp | да
textDocument/ссылки | да
textDocument/documentHighlight | да
textDocument/documentSymbol | да
textDocument и форматирование | да
textDocument/rangeFormatting | да
textDocument/onTypeFormatting |
textDocument или определения | да
textDocument/codeAction | да
textDocument/codeLens |
codeLens или исправить |
textDocument/documentLink |
documentLink или исправить |
textDocument и rename | да

## <a name="getting-started"></a>Начало работы

> [!NOTE]
> Начиная с Visual Studio 15.8 предварительной версии 3, поддержка распространенных протоколом языкового сервера встроены в Visual Studio.  Если вы создали с помощью предварительной версии расширений LSP [языка сервера клиента VSIX](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) версии, больше будет работать, как только для обновления до 15,8 предварительной версии 3 или более поздней версии.  Необходимо выполнить следующие действия для получения расширений LSP работать снова:
>
> 1. Удалите Microsoft Visual Studio язык сервера протокола предварительную версию VSIX.  Начиная с 15,8 предварительной версии 4, каждый раз при выполнении обновления в Visual Studio, мы автоматически обнаружит и удалить VSIX для вас в процессе обновления.
>
> 2. Обновите Справочник Nuget до последней версии не предварительного просмотра для [LSP пакеты](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client).
>
> 3. Удалите зависимость, приведенную в Microsoft Visual Studio язык сервера протокола Preview VSIX в манифесте VSIX.
>
> 4. Убедитесь, что VSIX указывает Visual Studio 15.8 предварительной версии 3 в качестве нижней границы для целевого объекта установки.
>
> 5. Перестройте и повторно развернуть.

### <a name="create-a-vsix-project"></a>Создайте проект VSIX

Чтобы создать расширение службы языка, с помощью сервера язык на основе LSP, сначала убедитесь, что у вас есть **разработка расширений Visual Studio** установить свой экземпляр VS рабочую нагрузку.

Затем создать новый пустой VSIXProject, перейдя по адресу **файл** > **новый проект** > **Visual C#**  >   **Расширяемость** > **проект VSIX**:

![Создайте проект vsix](media/lsp-vsix-project.png)

Для предварительной версии VS поддержка LSP будет в виде VSIX ([Microsoft.VisualStudio.LanguageServer.Client.Preview](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)). Разработчики расширений, которые хотят создать расширение с помощью серверов LSP языка необходимо зависимость от этой VSIX. Таким образом, клиенты, желающие Установка расширения языка сервера **необходимо сначала установить VSIX предварительной версии языка сервера протокола клиента.**

Чтобы задать зависимость VSIX, откройте конструктор манифеста VSIX для VSIX (двойным щелчком *source.extension.vsixmanifest* файла проекта) и перейдите к **зависимости**:

![Добавьте ссылку на язык сервера протокола клиента](media/lsp-reference-lsp-dependency.png)

Создание новой зависимости следующим образом:

![Определение языка сервера протокола клиента зависимости](media/lsp-define-lsp-dependency.png)

* **Источник**: вручную
* **Имя**: предварительная версия клиента протокола Server языка
* **Идентификатор**: Microsoft.VisualStudio.LanguageServer.Client.Preview
* **Диапазон версий**: [1.0,2.0)
* **Каков разрешения зависимости**: установлено пользователем
* **URL-адрес скачивания**: [https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)

> [!NOTE]
> **URL-адрес скачивания** должно быть заполнено, чтобы пользователи, Установка расширения могли установить необходимые зависимости.

### <a name="language-server-and-runtime-installation"></a>Установка сервера и среды выполнения языка

По умолчанию расширений, созданных для поддержки языка на основе LSP серверов в Visual Studio не будет содержать самих серверов языка и среды выполнения, необходимые для их выполнения. Разработчики расширений несут ответственность за распределение серверов языка и среды выполнения требуется. Существует несколько способов для этого:

* Язык серверов можно включить в VSIX файлы содержимого.
* Создание MSI-ФАЙЛ для установки языка сервера и/или необходимости сред выполнения.
* Приведены инструкции по Marketplace о том, что пользователи, как получить серверы сред выполнения и языка.

### <a name="textmate-grammar-files"></a>Файлы грамматики TextMate

LSP, не поддерживает спецификацию на способ обеспечения цветовое выделение текста для языков. Чтобы предоставить пользовательские цветовое выделение для языков в Visual Studio, разработчики расширений можно использовать файл грамматики TextMate. Чтобы добавить пользовательские файлы грамматики или темы TextMate, выполните следующие действия.

1. Создайте папку с именем «Грамматики» внутри расширения (или может быть любое имя).

2. Внутри *грамматики* папки, содержащие любые  *\*.tmlanguage*,  *\*plist-файл в*,  *\*.tmtheme*, или  *\*.json* файлы, хотелось бы, которые предоставляет пользовательские окрашивание.

3. Щелкните правой кнопкой мыши файлы, а затем выберите **свойства**. Изменение **построения** действие **содержимого** и **включить в VSIX** присваивается значение true.

4. Создание *.pkgdef* файл и добавьте строку, аналогичную следующей:

  ```xml
  [$RootKey$\TextMate\Repositories]
  "MyLang"="$PackageFolder$\Grammars"
  ```

5. Щелкните правой кнопкой мыши файлы, а затем выберите **свойства**. Изменение **построения** действие **содержимого** и **включить в VSIX** присваивается значение true.

После завершения предыдущих шагов, *грамматики* добавляется папка для установки пакета каталог как источник репозитория с именем «MyLang» («MyLang» — это имя для устранения неоднозначности и может принимать любую уникальную строку). Все грамматики (*.tmlanguage* файлы) и файлы тем (*.tmtheme* файлы) в этом каталоге будут применены как потенциальные и они имеют приоритет над встроенные грамматики TextMate в состав. Если объявленный расширения файла грамматики соответствует расширению открытого файла, TextMate зайдет.

## <a name="create-a-simple-language-client"></a>Создание простой язык клиента

### <a name="main-interface---ilanguageclientdotnetapimicrosoftvisualstudiolanguageserverclientilanguageclientviewvisualstudiosdk-2017"></a>Основной интерфейс - [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

После создания проекта VSIX, добавляемого в проект следующие пакеты NuGet:

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> При принимает зависимость от пакета NuGet после выполнения предыдущих шагов, в проект также добавляются Newtonsoft.Json и StreamJsonRpc пакеты. **Эти пакеты не обновляются, если вы уверены, что эти новые версии будут устанавливаться на версии Visual Studio, для которых предназначено расширение**. Сборки не будут включены в VSIX — вместо этого они считываются из каталога установки Visual Studio. Если вы ссылаетесь на более новую версию сборки, чем установленных на компьютере пользователя, расширение *не будет работать*.

Затем можно создать новый класс, реализующий [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) интерфейса, основной интерфейс, необходимый для языка клиентов, подключающихся к серверу язык на основе LSP.

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

Основные методы, которые должны быть реализованы [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) и [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017). [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) вызывается при загрузке расширения Visual Studio и Готово к запуску язык сервера. В этот метод можно вызывать [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) делегат немедленно, для обозначения языка сервер должен быть запущен, или можно выполнить дополнительную логику и вызвать [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) позже. **Чтобы активировать сервер языка, необходимо вызвать StartAsync в определенный момент.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) — это метод, в конечном счете вызывается путем вызова [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) делегировать; он содержит логику для запуска языка сервера и установить подключение к нему. Объект соединения, содержащий потоками для записи на сервер и чтения на сервере должен быть возвращен. Все исключения будут перехватываться и отображаться для пользователя с помощью сообщения об информационной панели в Visual Studio.

### <a name="activation"></a>Активация

После реализации языка клиентском классе необходимо определить два атрибута для того, чтобы определить, как он будет загружен в Visual Studio и активации:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio использует [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) для управления точки расширения. [Экспорт](https://msdn.microsoft.com/library/system.componentmodel.composition.exportattribute(v=vs.110).aspx) атрибут указывает Visual Studio, что выбраны как точку расширения этого класса и они будут загружены в соответствующее время.

Чтобы использовать MEF, необходимо также определить MEF как ресурс в манифесте VSIX.

Откройте конструктор манифеста VSIX и перейдите к **активы** вкладке:

![Добавить ресурс MEF](media/lsp-add-asset.png)

Щелкните, чтобы создать новый ресурс:

![Определение ресурса MEF](media/lsp-define-asset.png)

* **Тип**: Microsoft.VisualStudio.MefComponent
* **Источник**: проект в текущем решении
* **Проект**: [проект]

### <a name="content-type-definition"></a>Определение типа содержимого

В настоящее время единственным способом загрузить ваш язык на основе LSP серверный модуль является тип содержимого файла. То есть при определении вашего клиентского класса языка (который реализует [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)), необходимо определить типы файлы, при открытии, вызовет расширение для загрузки. Если открыты нет файлов, которые соответствуют вашей определенный тип содержимого, решение не будет загружено.

Это осуществляется путем определения одного или нескольких классов ContentTypeDefinition:

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

В предыдущем примере создается определение типа содержимого для файлов, которые заканчиваются на *.bar* расширение файла. Определение типа содержимого присваивается имя «строка» и **необходимо** являются производными от [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017).

После добавления определения типа содержимого, можно определить причины для загрузки клиента расширение языка в классе клиента языка:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

Добавление поддержки для языка серверов LSP не требуется реализовать систему проектов в Visual Studio. Клиенты можно открыть один файл или папку в Visual Studio, чтобы приступить к использованию службы вашего языка. На самом деле поддержка серверов языка LSP предназначен для работы только в сценариях, откройте папку или файл. Если реализован системе пользовательских проектов, некоторые компоненты (например, параметры) не будут работать.

## <a name="advanced-features"></a>Дополнительные возможности

### <a name="settings"></a>Параметры

Настраиваемые параметры языка сервера поддерживается, но это еще не закончили процесс улучшаются. Параметры относятся к что сервер языка поддерживает и обычно управлять как язык сервер передает данные. Например server языка может иметь параметр максимального количества ошибок. Авторы расширений определит значение по умолчанию, который может быть изменен пользователями для конкретных проектов.

Выполните следующие действия для добавления поддержки для параметров расширения LSP языковой службы.

1. Добавить в JSON-файл (например, *MockLanguageExtensionSettings.json*) в проекте, который содержит параметры и их значения по умолчанию. Пример:

  ```json
  {
    "foo.maxNumberOfProblems": -1
  }
  ```
2. Щелкните правой кнопкой мыши на JSON-файл и выберите **свойства**. Изменение **построения** действие «Content» и «включить в VSIX "присваивается значение true.

3. Реализовать ConfigurationSections и возвращения списка префиксов для параметров, определенных в JSON-файле (в Visual Studio Code, это будет указывать имя раздела конфигурации в файле package.json):

  ```csharp
  public IEnumerable<string> ConfigurationSections
  {
      get
      {
          yield return "foo";
      }
  }
  ```
4. Добавьте файл pkgdef в проект (Добавить новый текстовый файл и измените расширение файла на .pkgdef). Файл pkgdef должен содержать эти сведения:

  ```xml
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
  ```

5. Щелкните правой кнопкой файл pkgdef и выберите **свойства**. Изменение **построения** действие **содержимого** и **включить в VSIX** присваивается значение true.

6. Откройте *source.extension.vsixmanifest* файл и добавьте ресурс в **активов** вкладке:

  ![Редактирование активов vspackage](media/lsp-add-vspackage-asset.png)

  * **Тип**: Microsoft.VisualStudio.VsPackage
  * **Источник**: файл в файловой системе
  * **Путь**: [путь к вашей *.pkgdef* файл]

### <a name="user-editing-of-settings-for-a-workspace"></a>Изменение параметров для рабочей области пользователя

1. Пользователь открывает рабочей области, содержащей файлы, которому принадлежит сервер.
2. Пользователь добавляет файл в *.vs* папку с именем *VSWorkspaceSettings.json*.
3. Пользователь добавляет строки в *VSWorkspaceSettings.json* файла для параметра, предоставляемые сервером. Пример:

  ```json
  {
    "foo.maxNumberOfProblems": 10
  }
  ```
### <a name="enabling-diagnostics-tracing"></a>Включение трассировки диагностики
Для вывода всех сообщений между клиентом и сервером, что может оказаться полезным при отладке проблем можно включить трассировку диагностики.  Чтобы включить диагностическую трассировку, выполните следующие действия.

1. Откройте или создайте файл параметров рабочей области *VSWorkspaceSettings.json* (см. в разделе «Пользователь редактирует параметров для рабочей области»).
2. Добавьте следующую строку в файле параметров json:

```json
{
    "foo.trace.server": "Off"
}
```

Существует три возможных значения для уровень детализации трассировки:
* «Off»: полностью отключить трассировку
* «Messages»: трассировка включена, но единственный метод идентификатор имени и ответа отслеживаются.
* «Verbose»: трассировка включена; Это событие регистрируется сообщение целиком rpc.

Когда трассировка включается содержимое записывается в файл в *%temp%\VisualStudio\LSP* каталога.  Журнал имеет формат именования *[LanguageClientName]-[меткой времени] .log*.  В настоящее время трассировку можно включить только для сценариев, открыть папку.  Открытие одного файла для активации сервера языка отсутствует поддержка трассировки диагностики.

### <a name="custom-messages"></a>Пользовательские сообщения

Существуют API-интерфейсы на месте для упрощения передачи сообщений и получения сообщений от языка сервера, которые не являются частью стандартного протокола язык сервера. Для обработки пользовательских сообщений, реализовать [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) интерфейс в клиентском классе языка. [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) библиотека используется для передачи пользовательских сообщений между языка клиента и сервера языка. Так как расширение языка клиента LSP — так же, как и любое другое расширение Visual Studio, можно добавить дополнительные функции (которые не поддерживаются LSP) для Visual Studio (с помощью других API-интерфейсы Visual Studio) в расширении через пользовательские сообщения.

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

Чтобы отправить пользовательские сообщения на сервер языка, реализовать [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) метод [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017). Этот метод вызывается, когда сервер языка будет запущен и готов принимать сообщения. Объект [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) объект передается в качестве параметра, который затем можно сохранить для отправки сообщений на сервер языка с помощью [VS StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) API-интерфейсы. Пример ниже.

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

Иногда разработчик расширения может потребоваться перехват LSP сообщений, отправленных и полученных от языка сервера. Например разработчик расширения может для изменения параметра сообщения, отправляемого для определенного сообщения LSP или изменения результатов, возвращаемых с сервера языка для LSP возможности (например завершений). При необходимости расширения разработчики могут использовать MiddleLayer API для перехвата сообщений LSP.

Каждое сообщение LSP имеет свой собственный интерфейс серединным слоем для перехвата. Для перехвата определенного сообщения, создайте класс, реализующий интерфейс среднего уровня для данного сообщения. Затем запустите [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) интерфейс в клиентском классе языка и возврата экземпляра объекта в [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) свойство. Пример ниже.

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

Компонент среднего слоя, находится в разработке и еще не полный.

## <a name="sample-lsp-language-server-extension"></a>Пример LSP языка сервера расширения

Чтобы просмотреть исходный код образца расширения с помощью LSP клиентского API-интерфейса в Visual Studio, см. в разделе примеры VSSDK-расширения [LSP образец](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol).

## <a name="faq"></a>часто задаваемые вопросы

**Я хочу создать систему пользовательский проект, в дополнение к серверу LSP языка для предоставления более широкие поддержке компонентов в Visual Studio, как перейти об этой процедуре?**

Поддержка языка на основе LSP серверов в Visual Studio использует [функция "Открыть папку"](https://blogs.msdn.microsoft.com/visualstudio/2016/04/12/open-any-folder-with-visual-studio-15-preview/) и специально разработан для требует системе пользовательских проектов. Можно создать собственную систему пользовательский проект, следуя инструкциям [здесь](https://github.com/Microsoft/VSProjectSystem), но некоторые функции, такие как параметры, может не работать. — Логика инициализации по умолчанию для серверов LSP языка для передачи в расположение корневой папки, папки открытых в данный момент, поэтому если вы используете системе пользовательских проектов, может потребоваться предоставить пользовательскую логику во время инициализации, чтобы убедиться, вы можете языка сервера Запустите надлежащим образом.

**Как добавить поддержку отладчика?**

Мы предоставим поддержку [Общие, отладка протокола](https://code.visualstudio.com/docs/extensionAPI/api-debugging) в будущем выпуске.

**Если уже VS поддерживаемого языка установлена служба (например, JavaScript), по-прежнему установить расширение языка сервера LSP, предлагает дополнительные возможности (например, анализ кода)?**

Да, но не все компоненты будут работать должным образом. Конечной целью для серверных расширений языка LSP — включить службы языка, изначально не поддерживается в Visual Studio. Можно создавать расширения, которые обеспечивают дополнительную поддержку, с помощью серверов языка LSP, но некоторые функции (например, технология IntelliSense) будут беспроблемную работу. В общем случае рекомендуется использования серверных расширений языка LSP для предоставления новых возможностей языка, не расширения существующих.

**Где опубликовать серверу языка завершенного LSP VSIX?**

См. в инструкциях Marketplace [здесь](walkthrough-publishing-a-visual-studio-extension.md).
