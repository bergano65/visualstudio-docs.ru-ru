---
title: "Практическое руководство: предоставить службы асинхронной Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Практическое руководство: предоставить службы асинхронной Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Если вы хотите получить службу без блокирования потока пользовательского интерфейса, необходимо создать асинхронную службу и загрузить пакет в фоновом потоке. Для этой цели можно использовать <xref:Microsoft.VisualStudio.Shell.AsyncPackage> вместо <xref:Microsoft.VisualStudio.Shell.Package>, и добавить службу с помощью специальных асинхронных методов асинхронного пакета  
  
 Сведения о предоставлении синхронной службы Visual Studio в разделе [Практическое руководство: предоставления службы](../extensibility/how-to-provide-a-service.md).  
  
## Реализация асинхронной службе  
  
1.  Создайте проект VSIX \(**файл \/ New \/ Project или Visual C\# и Extensiblity и проект VSIX**\). Назовите проект **TestAsync**.  
  
2.  Добавьте в проект VSPackage. Выберите узел проекта в **обозревателе решений** и нажмите кнопку **Добавить \/ Создание элемента или элементы Visual C\# или расширения или пакета Visual Studio**. Этому файлу имя **TestAsyncPackage.cs**.  
  
3.  В TestAsyncPackage.cs внести изменения в пакет для наследования от AsyncPackage, а не пакет:  
  
    ```c#  
    public sealed class TestAsyncPackage : AsyncPackage  
    ```  
  
4.  Для реализации службы, необходимо создать три типа:  
  
    -   Интерфейс, который описывает службу. Многие из этих интерфейсов пусты, то есть, они имеют методы не.  
  
    -   Интерфейс, который описывает интерфейс службы. Этот интерфейс содержит методы, которые должны быть реализованы.  
  
    -   Класс, реализующий интерфейс службы и службы.  
  
5.  Пример очень простой реализации трех типов. Конструктор класса службы необходимо задать поставщика услуг. В этом примере мы просто добавим службы в файл кода пакета.  
  
6.  Добавьте следующие операторы using в файл пакета:  
  
    ```c#  
    using System.Threading;  
    using System.Threading.Tasks;  
    using System.Runtime.CompilerServices;  
    using System.IO;  
    ```  
  
7.  Вот реализация асинхронной службы. Обратите внимание, что установка асинхронный доступ к службе, а не синхронный доступ к службе в конструкторе:  
  
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
  
## Регистрация службы  
 Чтобы зарегистрировать службу, добавьте <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> для пакета, который предоставляет службу. Существует два отличия от синхронной службы регистрации.  
  
-   Если вы являетесь Автозагрузка пакета, необходимо добавить <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> BackgroundLoad значение атрибута. Дополнительные сведения о Автозагрузка VSPackages. в разделе [Загрузка пакетов VSPackages](../extensibility/loading-vspackages.md).  
  
-   Необходимо добавить **AllowsBackgroundLoading \= true** на <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>. Дополнительные сведения о PackageRegistrationAttribute см. в разделе [Регистрация и Отмена регистрации VSPackages.](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Вот пример AsyncPackage с регистрацией асинхронную службу::  
  
```c#  
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]  
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]   
[Guid(TestAsyncPackage.PackageGuidString)]  
public sealed class TestAsyncPackage : AsyncPackage  
{. . . }  
```  
  
## Добавление службы  
  
1.  В TestAsyncPackage.cs, удалите `Initialize()` метод и переопределение `InitializeAsync()` метод. Добавьте службу и добавьте метод обратного вызова для создания служб. Ниже приведен пример асинхронной инициализатора Добавление службы:  
  
    ```  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
2.  Добавьте ссылку на Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll.  
  
3.  Реализуйте метод обратного вызова в виде асинхронного метода, который создает и возвращает службы.  
  
    ```c#  
    public async System.Threading.Tasks.Task<object> CreateService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)  
    {  
        STextWriterService service = null;  
        await System.Threading.Tasks.Task.Run(() => {  
                    service = new TextWriterService(this);  
             });  
  
        return service;  
    }  
  
    ```  
  
## С помощью службы  
 Теперь можно получить службу и использовать его методы.  
  
1.  Мы покажем это инициализатор, но можно получить службу в любом месте вы хотите использовать службу.  
  
    ```c#  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await writer.WriteLineAsync(<userpath>), "this is a test");  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
     Не забудьте изменить *\< userpath \>* имя файла и путь, который имеет смысл на компьютере\!  
  
2.  Постройте и запустите его. Когда появится в экспериментальном экземпляре Visual Studio, откройте решение. В результате AsyncPackage для автозагрузки. При выполнения инициализатор, следует найти файл в указанном месте.  
  
## Использование асинхронной службе в обработчик команд  
 Ниже приведен пример того, как использовать асинхронную службу в команде меню. Можно использовать для использования службы в других\-асинхронных методов, приведенных здесь.  
  
1.  Добавление команды меню в проект. \(В **обозревателе решений**, выберите узел проекта правой кнопкой мыши и выберите **Добавить\-новый элемент и расширяемость \/ пользовательских команд**.\) Имя командного файла **TestAsyncCommand.cs.**  
  
2.  Шаблон пользовательскую команду повторно добавляет `Initialize()` метод в файл TestAsyncPackage.cs для инициализации команды. В метод Initialize\(\) Скопируйте строку, которая инициализирует команды. Он должен выглядеть следующим образом:  
  
    ```  
    TestAsyncCommand.Initialize(this);  
    ```  
  
     Переместите эту строку, чтобы `InitializeAsync()` метод в файле AsyncPackageForService.cs. Так как это асинхронная инициализация, необходимо переключиться в основной поток без инициализации команды с помощью <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Теперь он должен выглядеть следующим образом:  
  
    ```c#  
  
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
  
3.  Удалить `Initialize()` метод.  
  
4.  Найдите в файле TestAsyncCommand.cs `MenuItemCallback()` метод. Удаление тела метода.  
  
5.  Добавить с помощью инструкции:  
  
    ```  
    using System.IO;  
    ```  
  
6.  Добавить асинхронный метод с именем `GetAsyncService()`, который возвращает службы и использует его методы:  
  
    ```c#  
    private async System.Threading.Tasks.Task GetAsyncService()  
    {  
        ITextWriterService textService =   
           this.ServiceProvider.GetService(typeof(STextWriterService))  
              as ITextWriterService;  
        // don’t forget to change <userpath> to a local path  
        await writer.WriteLineAsync((<userpath>),"this is a test");  
       }  
  
    ```  
  
7.  Вызовите этот метод из `MenuItemCallback()` метод:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        GetAsyncService();  
    }  
  
    ```  
  
8.  Постройте решение и запустить отладку. Когда появится в экспериментальном экземпляре Visual Studio, перейдите к **средства** меню и найти **вызова TestAsyncCommand** элемент меню. Если щелкнуть его, TextWriterService записывает в указанный файл. \(Не требуется для открытия решения, так как команда также в результате вызова пакета для загрузки.\)  
  
## См. также  
 [Использование и предоставления услуг](../extensibility/using-and-providing-services.md)