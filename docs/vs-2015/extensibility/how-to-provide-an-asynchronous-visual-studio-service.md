---
title: Руководство. предоставление асинхронной службы | Документация Майкрософт
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0c58b0be10bf10a21b783a48d52806bf769381ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204105"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Практическое руководство. Предоставление асинхронной службы Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если вы хотите получить службу, не блокируя поток пользовательского интерфейса, следует создать асинхронную службу и загрузить пакет в фоновом потоке. Для этой цели можно использовать <xref:Microsoft.VisualStudio.Shell.AsyncPackage> вместо <xref:Microsoft.VisualStudio.Shell.Package> и добавить службу с особыми асинхронными методами асинхронного пакета.

 Сведения о предоставлении синхронных служб Visual Studio см. [в разделе руководство. предоставление службы](../extensibility/how-to-provide-a-service.md).

## <a name="implementing-an-asynchronous-service"></a>Реализация асинхронной службы

1. Создайте проект VSIX (**File/New/Project/Visual C#/расширяемости/VSIX Project**). Назовите проект **тестасинк**.

2. Добавьте VSPackage в проект. Выберите узел проекта в **Обозреватель решений** и щелкните **Добавить/создать элемент/Visual C# элементы/Расширяемость/пакет Visual Studio**. Назовите этот файл **TestAsyncPackage.CS**.

3. В TestAsyncPackage.cs измените пакет, чтобы он наследовался от AsyncPackage, а не пакета.

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Чтобы реализовать службу, необходимо создать три типа:

    - Интерфейс, описывающий службу. Многие из этих интерфейсов пусты, т. е. у них нет методов.

    - Интерфейс, описывающий интерфейс службы. Этот интерфейс включает методы, которые должны быть реализованы.

    - Класс, реализующий как службу, так и интерфейс службы.

5. В следующем примере показана базовая реализация трех типов. Конструктор класса службы должен задать поставщик службы. В этом примере мы просто добавим службу в файл кода пакета.

6. Добавьте следующие операторы using в файл пакета:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    ```

7. Ниже приведена реализация асинхронной службы. Обратите внимание, что вместо синхронного поставщика служб в конструкторе необходимо задать поставщик асинхронной службы:

    ```
    public class TextWriterService : STextWriterService, ITextWriterService
    {
        private Microsoft.VisualStudio.Shell.IAsyncServiceProvider serviceProvider;
        public TextWriterService(Microsoft.VisualStudio.Shell.IAsyncServiceProvider provider)
        {
            serviceProvider = provider;
        }
        public async System.Threading.Tasks.Task WriteLineAsync(string path, string line)
        {
            StreamWriter writer = new StreamWriter(path);
            await writer.WriteLineAsync(line);
            writer.Close();
        }
        public TaskAwaiter GetAwaiter()
        {
            return new TaskAwaiter();
        }
    }
    public interface STextWriterService
    {
    }
    public interface ITextWriterService
    {
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);
        TaskAwaiter GetAwaiter();
    }
    ```

## <a name="registering-a-service"></a>Регистрация службы
 Чтобы зарегистрировать службу, добавьте в <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> пакет, предоставляющий службу. Регистрация синхронной службы состоит из двух отличий:

- При автозагрузке пакета необходимо добавить <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> значение баккграундлоад к атрибуту. Дополнительные сведения об автозагрузке пакетов VSPackage см. в разделе [Загрузка пакетов VSPackage](../extensibility/loading-vspackages.md).

- Необходимо добавить поле **алловсбаккграундлоадинг = true** в <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> . Дополнительные сведения о Паккажерегистратионаттрибуте см. в разделе [Регистрация пакетов VSPackage и их отмена](../extensibility/registering-and-unregistering-vspackages.md).

  Ниже приведен пример AsyncPackage с асинхронной регистрацией службы:.

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="adding-a-service"></a>Добавление службы

1. В TestAsyncPackage.cs удалите `Initialize()` метод и переопределите `InitializeAsync()` метод. Добавьте службу и добавьте метод обратного вызова для создания служб. Ниже приведен пример асинхронного инициализатора, который добавляет службу:

    ```
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

2. Добавьте ссылку на Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll.

3. Реализуйте метод обратного вызова в качестве асинхронного метода, который создает и возвращает службу.

    ```csharp
    public async System.Threading.Tasks.Task<object> CreateService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        STextWriterService service = null;
        await System.Threading.Tasks.Task.Run(() => {
                    service = new TextWriterService(this);
             });

        return service;
    }

    ```

## <a name="using-a-service"></a>Использование службы
 Теперь вы можете получить службу и использовать ее методы.

1. Мы покажем это в инициализаторе, но вы можете получить службу в любом месте, где вы хотите использовать службу.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await writer.WriteLineAsync(<userpath>), "this is a test");

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

     Не забудьте перейти *\<userpath>* к имени файла и пути, которые имеют смысл на вашем компьютере!

2. Выполните сборку и запустите код. Когда появится экспериментальный экземпляр Visual Studio, откройте решение. Это приводит к тому, что AsyncPackage автозагрузки. При запуске инициализатора необходимо найти файл в указанном расположении.

## <a name="using-an-asynchronous-service-in-a-command-handler"></a>Использование асинхронной службы в обработчике команд
 Ниже приведен пример использования асинхронной службы в команде меню. Приведенную здесь процедуру можно использовать для использования службы в других неасинхронных методах.

1. Добавьте команду меню в проект. (В **Обозреватель решений**выберите узел проекта, щелкните его правой кнопкой мыши и выберите **команду Добавить/создать элемент/расширяемость/Настраиваемая команда**.) Назовите командный файл **TestAsyncCommand.cs.**

2. Пользовательский шаблон команды повторно добавляет `Initialize()` метод в файл TestAsyncPackage.cs, чтобы инициализировать команду. В методе Initialize () скопируйте строку, которая инициализирует команду. Он должен выглядеть так:

    ```
    TestAsyncCommand.Initialize(this);
    ```

     Переместите эту строку в `InitializeAsync()` метод в файле AsyncPackageForService.cs. Так как это асинхронная инициализация, необходимо переключиться на основной поток перед инициализацией команды с помощью <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> . Результат будет выглядеть так:

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        TestAsyncCommand.Initialize(this);

        this.AddService(typeof(STextWriterService), CreateService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await writer.WriteLineAsync((<userpath>, "this is a test");

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

3. Удалите `Initialize()` метод.

4. В файле TestAsyncCommand.cs найдите `MenuItemCallback()` метод. Удалите текст метода.

5. Добавьте инструкцию using:

    ```
    using System.IO;
    ```

6. Добавьте асинхронный метод с именем `GetAsyncService()` , который получает службу и использует ее методы:

    ```csharp
    private async System.Threading.Tasks.Task GetAsyncService()
    {
        ITextWriterService textService =
           this.ServiceProvider.GetService(typeof(STextWriterService))
              as ITextWriterService;
        // don’t forget to change <userpath> to a local path
        await writer.WriteLineAsync((<userpath>),"this is a test");
       }

    ```

7. Вызовите этот метод из `MenuItemCallback()` метода:

    ```
    private void MenuItemCallback(object sender, EventArgs e)
    {
        GetAsyncService();
    }

    ```

8. Постройте решение и запустите отладку. Когда появится экспериментальный экземпляр Visual Studio, перейдите в меню **Сервис** и найдите пункт меню **вызвать тестасинккомманд** . Если щелкнуть его, Текствритерсервице запишет в указанный файл. (Не нужно открывать решение, так как вызов команды также вызывает загрузку пакета.)

## <a name="see-also"></a>См. также:
 [Использование и предоставление служб](../extensibility/using-and-providing-services.md)
