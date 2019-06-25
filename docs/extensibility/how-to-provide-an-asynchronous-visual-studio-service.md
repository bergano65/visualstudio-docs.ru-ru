---
title: Практическое руководство. Предоставляет службу для асинхронных Visual Studio | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ebba3ca9434d704fff25f3d3519748930db12aa7
ms.sourcegitcommit: 34807a6b6105ae7839adde8ff994c85182ad3aff
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/24/2019
ms.locfileid: "67342396"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Практическое руководство. Предоставить асинхронной службы Visual Studio
Если вы хотите получить службы без блокировки потока пользовательского интерфейса, необходимо создать асинхронный и загрузить пакет в фоновом потоке. Для этой цели можно использовать <xref:Microsoft.VisualStudio.Shell.AsyncPackage> вместо <xref:Microsoft.VisualStudio.Shell.Package>, добавьте службу с помощью специальных асинхронных методов асинхронной пакета.

 Сведения о предоставлении синхронной служб Visual Studio, см. в разделе [как: Предоставляет службу](../extensibility/how-to-provide-a-service.md).

## <a name="implement-an-asynchronous-service"></a>Реализовать асинхронный

1. Создайте проект VSIX (**файл** > **New** > **проекта** > **Visual C#**  >  **Артефактам** > **проект VSIX**). Назовите проект **TestAsync**.

2. Добавьте в проект VSPackage. Выберите узел проекта в **обозревателе решений** и нажмите кнопку **добавить** > **новый элемент** > **элементы Visual C#**  >  **Расширяемости** > **пакет Visual Studio**. Этот файл должен называться *TestAsyncPackage.cs*.

3. В *TestAsyncPackage.cs*, изменить идентификатор пакета для наследования от `AsyncPackage` вместо `Package`:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Чтобы реализовать службу, необходимо создать три типа:

    - Интерфейс, определяющий службу. Многие из этих интерфейсов пусты, то есть они имеют методы не так, как они используются только для выполнения запросов к службе.

    - Интерфейс, который описывает интерфейс службы. Этот интерфейс содержит методы, которые должны быть реализованы.

    - Класс, реализующий интерфейс службы и службы.

5. В следующем примере простейшую реализацию из трех типов. Конструктор класса службы необходимо задать поставщик услуг. В этом примере мы просто добавим службы к файлу пакета кода.

6. Добавьте следующие операторы using в файл пакета:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. Ниже показана реализация асинхронной службы. Обратите внимание на то, что необходимо установить поставщик асинхронная служба, а не синхронный доступ к службе в конструкторе:

    ```csharp
    public class TextWriterService : STextWriterService, ITextWriterService
    {
        private IAsyncServiceProvider asyncServiceProvider;

        public TextWriterService(IAsyncServiceProvider provider)
        {
            // constructor should only be used for simple initialization
            // any usage of Visual Studio service, expensive background operations should happen in the
            // asynchronous InitializeAsync method for best performance
            asyncServiceProvider = provider;
        }

        public async Task InitializeAsync(CancellationToken cancellationToken)
        {
            await TaskScheduler.Default;
            // do background operations that involve IO or other async methods

            await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
            // query Visual Studio services on main thread unless they are documented as free threaded explicitly.
            // The reason for this is the final cast to service interface (such as IVsShell) may involve COM operations to add/release references.

            IVsShell vsShell = this.asyncServiceProvider.GetServiceAsync(typeof(SVsShell)) as IVsShell;
            // use Visual Studio services to continue initialization
        }

        public async Task WriteLineAsync(string path, string line)
        {
            StreamWriter writer = new StreamWriter(path);
            await writer.WriteLineAsync(line);
            writer.Close();
        }
    }

    public interface STextWriterService
    {
    }

    public interface ITextWriterService
    {
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);
    }
    ```

## <a name="register-a-service"></a>Регистрация службы
 Чтобы зарегистрировать службу, добавьте <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> к пакету, который предоставляет службу. Различные регистрация синхронной службы, необходимо убедитесь, что пакет и служба поддерживает асинхронной загрузки:

- Необходимо добавить **AllowsBackgroundLoading = true** поле <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> чтобы пакета можно асинхронно инициализировать Дополнительные сведения о PackageRegistrationAttribute, см. в разделе [регистрации и Отмена регистрации пакетов VSPackage](../extensibility/registering-and-unregistering-vspackages.md).

- Необходимо добавить **IsAsyncQueryable = true** поле <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> чтобы экземпляр службы, может инициализироваться в асинхронном режиме.

  Ниже приведен пример `AsyncPackage` с регистрацию асинхронная служба:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>Добавление службы

1. В *TestAsyncPackage.cs*, удалите `Initialize()` метод и переопределение `InitializeAsync()` метод. Добавьте службу и метод обратного вызова для создания служб. Вот пример асинхронной инициализатора, добавление службы:

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```

2. Добавьте ссылку на *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll*.

3. Реализуйте метод обратного вызова как асинхронный метод, который создает и возвращает службе.

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>Использование службы
 Теперь можно получить службу и использовать его методы.

1. Мы покажем это в инициализаторе, но вы можете получить службу в любом месте вы хотите использовать службу.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
    }

    ```

     Не забудьте изменить `userpath` имя файла и путь, который лучше всего подходит на вашем компьютере!

2. Постройте и запустите код. Когда появится в экспериментальном экземпляре Visual Studio, откройте решение. В результате `AsyncPackage` Настройка автоматической загрузки. При запуске инициализатора следует найти файл в указанном расположении.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Используйте асинхронный в обработчике команд
 Вот пример того, как использовать службу асинхронной команды меню. Можно использовать для использования службы в других-асинхронных методов, приведенных здесь.

1. Добавьте команду меню в проект. (В **обозревателе решений**, выберите узел проекта, щелкните правой кнопкой мыши и выберите **добавить** > **новый элемент**  >   **Расширяемость** > **пользовательской команды**.) Имя командного файла *TestAsyncCommand.cs*.

2. Шаблон пользовательской команды повторно добавляет `Initialize()` метод *TestAsyncPackage.cs* файл для инициализации команды. В `Initialize()` метод, скопируйте строку, которая инициализирует команды. Он должен выглядеть так:

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     Переместить эту строку, чтобы `InitializeAsync()` метод в *AsyncPackageForService.cs* файла. Так как это в асинхронную инициализацию, необходимо переключиться на основной поток до инициализации команды с помощью <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Теперь он должен выглядеть следующим образом:

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");

        await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
        TestAsyncCommand.Initialize(this);
    }

    ```

3. Удалить `Initialize()` метод.

4. В *TestAsyncCommand.cs* найдите `MenuItemCallback()` метод. Удалите тело метода.

5. Добавьте инструкцию using:

    ```csharp
    using System.IO;
    ```

6. Добавить асинхронный метод с именем `UseTextWriterAsync()`, который получает службы и использует его методы:

    ```csharp
    private async System.Threading.Tasks.Task UseTextWriterAsync()
    {
        // Query text writer service asynchronously to avoid a blocking call.
        ITextWriterService textService =
           await AsyncServiceProvider.GlobalProvider.GetServiceAsync(typeof(STextWriterService))
              as ITextWriterService;

        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
       }

    ```

7. Вызовите этот метод из `MenuItemCallback()` метод:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. Постройте решение и запустите отладку. Когда Откроется экспериментальный экземпляр Visual Studio, перейдите к **средства** меню и найти **вызова TestAsyncCommand** пункта меню. Если щелкнуть его, TextWriterService Записывает указанный файл. (Не нужно открыть решение, так как при вызове команды также приводит к загрузке пакета.)

## <a name="see-also"></a>См. также
- [Использование и предоставление сервисов](../extensibility/using-and-providing-services.md)
