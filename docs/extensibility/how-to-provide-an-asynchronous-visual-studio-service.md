---
title: "Как: предоставляет службу асинхронной Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1bcf34f730411589624075bde4ace0b5457e07a7
ms.sourcegitcommit: f36eb7f989efbdbed0d0a087afea8ffe27d8ca15
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2017
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Как: предоставляет службу асинхронной Visual Studio
Если вы хотите получить службу без блокировки потока пользовательского интерфейса, необходимо создать асинхронную службу и загрузить пакет в фоновом потоке. Для этой цели можно использовать <xref:Microsoft.VisualStudio.Shell.AsyncPackage> вместо <xref:Microsoft.VisualStudio.Shell.Package>и добавление службы с асинхронной пакета специальные асинхронных методов  
  
 Сведения об обслуживании синхронной Visual Studio см. в разделе [как: обслуживать](../extensibility/how-to-provide-a-service.md).  
  
## <a name="implementing-an-asynchronous-service"></a>Реализация асинхронной службы  
  
1.  Создайте проект VSIX (**файл > Создать > проект > Visual C# > Extensiblity > проект VSIX**). Назовите проект **TestAsync**.  
  
2.  Добавьте в проект VSPackage. Выберите узел проекта в **обозревателе решений** и нажмите кнопку **Добавить > новый элемент > элементы Visual C# > расширяемости > пакета Visual Studio**. Этому файлу имя **TestAsyncPackage.cs**.  
  
3.  В TestAsyncPackage.cs измените пакет для наследования от AsyncPackage, а не в пакет:  
  
    ```csharp  
    public sealed class TestAsyncPackage : AsyncPackage  
    ```  
  
4.  Чтобы реализовать службу, необходимо создать три типа:  
  
    -   Интерфейс, который описывает службу. Многие из этих интерфейсов пусты, то есть, они имеют нет методов.  
  
    -   Интерфейс, который описывает интерфейс службы. Этот интерфейс содержит методы, которые должны быть реализованы.  
  
    -   Класс, реализующий службу и интерфейс службы.  
  
5.  Пример очень простой реализации трех типов. Конструктор для класса службы необходимо установить поставщик услуг. В этом примере просто будет добавлен в пакет файл кода службы.  
  
6.  Добавьте следующие инструкции using файл пакета:  
  
    ```csharp  
    using System.Threading;  
    using System.Threading.Tasks;  
    using System.Runtime.CompilerServices;  
    using System.IO;  
    ```  
  
7.  Вот реализация асинхронной службы. Обратите внимание, что необходимо задать в конструкторе асинхронный доступ к службе, а не синхронный доступ к службе.  
  
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
 Чтобы зарегистрировать службу, добавьте <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> для пакета, предоставляющего службу. Существует два отличия от регистрации синхронной службы:  
  
-   Если вы являетесь Автозагрузка пакета, необходимо добавить <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> BackgroundLoad значение для атрибута. Дополнительные сведения о Автозагрузка пакеты VSPackage. в разделе [загрузке пакетов VSPackage](../extensibility/loading-vspackages.md).  
  
-   Необходимо добавить **AllowsBackgroundLoading = true** на <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>. Дополнительные сведения о PackageRegistrationAttribute см. в разделе [регистрация и Отмена регистрации пакетов VSPackage](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Ниже приведен пример AsyncPackage асинхронную службу регистрации в::  
  
```csharp  
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]  
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]   
[Guid(TestAsyncPackage.PackageGuidString)]  
public sealed class TestAsyncPackage : AsyncPackage  
{. . . }  
```  
  
## <a name="adding-a-service"></a>Добавление службы  
  
1.  В TestAsyncPackage.cs, удалите `Initialize()` метод и переопределение `InitializeAsync()` метод. Добавьте службу и метод обратного вызова для создания служб. Ниже приведен пример асинхронной инициализатора Добавление службы:  
  
    ```  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
2.  Добавьте ссылку на Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll.  
  
3.  Реализуйте метод обратного вызова как асинхронный метод, который создает и возвращает службе.  
  
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
  
## <a name="using-a-service"></a>С помощью службы  
 Теперь можно получить службу и использовать его методы.  
  
1.  Мы покажем это в инициализаторе, однако вы можете получить службу в любом месте необходимо использовать службу.  
  
    ```csharp  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await writer.WriteLineAsync(<userpath>), "this is a test");  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
     Не забудьте изменить  *\<userpath >* имя файла и путь, который имеет смысл на компьютере.  
  
2.  Постройте и запустите его. Когда Откроется экспериментальный экземпляр Visual Studio, откройте решение. В этом случае AsyncPackage для автозагрузки (AutoLoad). При запуске инициализатора должен находиться файл в указанном месте.  
  
## <a name="using-an-asynchronous-service-in-a-command-handler"></a>С помощью асинхронного службы в обработчике команды  
 Ниже приведен пример того, как использовать асинхронную службу в команде меню. Можно использовать приведенных здесь использовать службу в других — асинхронных методов.  
  
1.  Добавьте команду меню для проекта. (В **обозревателе решений**, выберите узел проекта, щелкните правой кнопкой мыши и выберите **добавить / новый элемент и расширяемость или в пользовательских командной**.) Имя файла команд **TestAsyncCommand.cs.**  
  
2.  Шаблон пользовательской команды повторно добавляет `Initialize()` метод файл TestAsyncPackage.cs для инициализации команды. В метод Initialize() скопируйте строки, которая инициализирует команды. Он должен выглядеть так:  
  
    ```  
    TestAsyncCommand.Initialize(this);  
    ```  
  
     Переместить эту строку, чтобы `InitializeAsync()` метод в файле AsyncPackageForService.cs. Так как это асинхронную инициализацию, необходимо перейти в основной поток до инициализации команды с помощью <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Он должен выглядеть следующим образом:  
  
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
  
3.  Удалить `Initialize()` метод.  
  
4.  Найдите в файле TestAsyncCommand.cs `MenuItemCallback()` метод. Удаление тела метода.  
  
5.  Добавить с помощью инструкции:  
  
    ```  
    using System.IO;  
    ```  
  
6.  Добавить асинхронный метод с именем `GetAsyncService()`, который получает службы и использует его методы:  
  
    ```csharp  
    private async System.Threading.Tasks.Task GetAsyncService()  
    {  
        ITextWriterService textService =   
           this.ServiceProvider.GetService(typeof(STextWriterService))  
              as ITextWriterService;  
        // don't forget to change <userpath> to a local path  
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
  
8.  Постройте решение и запустите отладку. Когда Откроется экспериментальный экземпляр Visual Studio, перейдите к **средства** меню и выполните поиск **TestAsyncCommand вызова** элемента меню. Если щелкнуть его, TextWriterService записывает в указанный файл. (Не требуется для открытия решения, так как команда также в результате вызова пакет для загрузки.)  
  
## <a name="see-also"></a>См. также  
 [Использование и предоставление служб](../extensibility/using-and-providing-services.md)