---
title: 'Как: Обеспечить асинхронную услугу визуальной студии (ru) Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65362e465beec5465903083beca069104a48166b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710758"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Как: Обеспечить асинхронный сервис Visual Studio
Если вы хотите получить услугу без блокировки потока uI, необходимо создать асинхронную службу и загрузить пакет на фоновый поток. Для этого можно использовать <xref:Microsoft.VisualStudio.Shell.AsyncPackage> вместо <xref:Microsoft.VisualStudio.Shell.Package>того, чтобы добавить услугу специальными асинхронными методами асинхронного пакета.

 Для получения информации о предоставлении синхронных услуг Visual Studio, [см.](../extensibility/how-to-provide-a-service.md)

## <a name="implement-an-asynchronous-service"></a>Внедрение асинхронного сервиса

1. Создать проект VSIX **(Файл** > **Новый** > **проект** > **Визуальный C '** > **Extensiblity** > **VSIX проекта**). Назовите проект **TestAsync**.

2. Добавьте в проект VSPackage. Выберите узла проекта в **Solution Explorer** и нажмите **Добавить** > **новый элемент** > **Visual C' Элементы** > **Расширяемый** > **Визуальный Studio пакет**. Назовите этот файл *TestAsyncPackage.cs*.

3. В *TestAsyncPackage.cs,* изменить пакет `AsyncPackage` наследовать `Package`от, а не :

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Для реализации службы необходимо создать три типа:

    - Интерфейс, идентифицирующие службу. Многие из этих интерфейсов пусты, то есть у них нет методов, так как они используются только для запроса службы.

    - Интерфейс, описывающий интерфейс службы. Этот интерфейс включает в себя методы, которые должны быть реализованы.

    - Класс, который реализует как службу, так и интерфейс службы.

5. Следующий пример показывает очень базовую реализацию трех типов. Конструктор класса услуг должен установить поставщика услуг. В этом примере мы просто добавим службу в файл кода пакета.

6. Добавьте следующие директивы с помощью в файл пакета:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. Вот асинхронная реализация службы. Обратите внимание, что необходимо установить в конструкторе асинхронного поставщика услуг, а не синхронного поставщика услуг:

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

            await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
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

## <a name="register-a-service"></a>Регистрация услуги
 Чтобы зарегистрировать услугу, <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> добавьте пакет, который предоставляет услугу. В зависимости от регистрации синхронной службы необходимо убедиться, что пакет и сервис поддерживают загрузку async:

- Вы должны добавить **AllowsBackgroundLoading - истинное** поле для обеспечения того, <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> чтобы пакет можно было асинхронно инициализовать для получения дополнительной информации о PackageRegistrationAttribute, см. [Регистрация и отменить регистрацию VSPackages.](../extensibility/registering-and-unregistering-vspackages.md)

- Необходимо добавить истинное поле <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> **IsAsync-queryable в** экземпляр обслуживания, чтобы обеспечить асинхронное инициирование экземпляра службы.

  Вот пример `AsyncPackage` с асинхронной регистрацией услуг:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>Добавление службы

1. В *TestAsyncPackage.cs,* `Initialize()` удалить метод и `InitializeAsync()` переопределить метод. Добавьте службу и добавьте метод обратного вызова для создания служб. Вот пример асинхронного инициализатора, добавляя услугу:

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```
    Чтобы сделать эту услугу видимой за пределами этого пакета, установите значение флага продвижения *в* качестве последнего параметра:`this.AddService(typeof(STextWriterService), CreateTextWriterService, true);`

2. Добавить ссылку на *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll*.

3. Реализация метода обратного откидывания в качестве асинхронного метода, который создает и возвращает службу.

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>Использование службы
 Теперь вы можете получить услугу и использовать ее методы.

1. Мы покажем это в инициаторе, но вы можете получить услугу в любом месте вы хотите воспользоваться услугой.

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

     Не забудьте изменить `userpath` имя файла и путь, который имеет смысл на вашей машине!

2. Создайте и запустите код. Когда появится экспериментальный экземпляр Visual Studio, откройте решение. Это приводит `AsyncPackage` к автоматической загрузке. При запуске инициализатора необходимо найти файл в указанном вами месте.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Используйте асинхронную службу в обработчике команд
 Вот пример использования асинхронной службы в команде меню. Вы можете использовать показанную здесь процедуру, чтобы использовать службу другими неасинхронными методами.

1. Добавьте команду меню в проект. (В **Solution Explorer**выберите узло проекта, нажмите правой кнопкой мыши и **выберите Добавить** > **новый элемент** > **Extensibility** > **Custom Command.)** Назовите файл команды *TestAsyncCommand.cs*.

2. Шаблон пользовательских команд повторно `Initialize()` добавляет метод в *TestAsyncPackage.cs* файл, чтобы инициализировать команду. В `Initialize()` методе скопируйте строку, которая инициирует команду. Результат будет выглядеть так:

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     Переместите `InitializeAsync()` эту строку в метод в *файле AsyncPackageForService.cs.* Так как это находится в асинхронной инициализации, вы должны <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>переключиться на основной поток, прежде чем инициализировать команду с помощью. Результат будет выглядеть так:

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

3. Удалите `Initialize()` метод.

4. В *TestAsyncCommand.cs* файле `MenuItemCallback()` найдите метод. Удалите тело метода.

5. Добавьте директиву:

    ```csharp
    using System.IO;
    ```

6. Добавьте асинхронный `UseTextWriterAsync()`метод под названием , который получает услугу и использует ее методы:

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

7. Вызовите этот `MenuItemCallback()` метод из метода:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. Постройте решение и запустите отладку. Когда появится экспериментальный экземпляр Visual Studio, перейдите в меню **Tools** и ищите элемент меню **Invoke TestAsyncCommand.** При нажатии на него TextWriterService пишет в указанный вами файл. (Вам не нужно открывать решение, потому что вызывая команду также вызывает загрузку пакета.)

## <a name="see-also"></a>См. также
- [Использование и предоставление услуг](../extensibility/using-and-providing-services.md)
