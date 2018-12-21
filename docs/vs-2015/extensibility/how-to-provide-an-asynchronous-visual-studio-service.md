---
title: 'Практическое: предоставляет службу для асинхронных Visual Studio | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4833fcef561bcc7c81a8c19fd5c4a1fcb2f7ccea
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51767635"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Практическое: предоставляет службу для асинхронных Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если вы хотите получить службы без блокировки потока пользовательского интерфейса, необходимо создать асинхронный и загрузить пакет в фоновом потоке. Для этой цели можно использовать <xref:Microsoft.VisualStudio.Shell.AsyncPackage> вместо <xref:Microsoft.VisualStudio.Shell.Package>, добавьте службу с помощью специальных асинхронных методов асинхронной пакета  
  
 Сведения о предоставлении синхронной служб Visual Studio, см. в разделе [как: предоставить службу](../extensibility/how-to-provide-a-service.md).  
  
## <a name="implementing-an-asynchronous-service"></a>Реализации асинхронной службы  
  
1.  Создайте проект VSIX (**файл / создать / проект / Visual C# / артефактам / проект VSIX**). Назовите проект **TestAsync**.  
  
2.  Добавьте в проект VSPackage. Выберите узел проекта в **обозревателе решений** и нажмите кнопку **добавить / новый элемент / элементы Visual C# / расширяемость / пакет Visual Studio**. Этот файл должен называться **TestAsyncPackage.cs**.  
  
3.  В TestAsyncPackage.cs измените наследование от AsyncPackage, а не пакета идентификатор пакета:  
  
    ```csharp  
    public sealed class TestAsyncPackage : AsyncPackage  
    ```  
  
4.  Чтобы реализовать службу, необходимо создать три типа:  
  
    -   Интерфейс, который описывает службу. Многие из этих интерфейсов пусты, то есть они имеют без методов.  
  
    -   Интерфейс, который описывает интерфейс службы. Этот интерфейс содержит методы, которые должны быть реализованы.  
  
    -   Класс, реализующий интерфейс службы и службы.  
  
5.  В следующем примере простейшую реализацию из трех типов. Конструктор класса службы необходимо задать поставщик услуг. В этом примере мы просто добавим службы к файлу пакета кода.  
  
6.  Добавьте следующие операторы using в файл пакета:  
  
    ```csharp  
    using System.Threading;  
    using System.Threading.Tasks;  
    using System.Runtime.CompilerServices;  
    using System.IO;  
    ```  
  
7.  Ниже показана реализация асинхронной службы. Обратите внимание на то, что необходимо установить поставщик асинхронная служба, а не синхронный доступ к службе в конструкторе:  
  
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
 Чтобы зарегистрировать службу, добавьте <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> к пакету, который предоставляет службу. Существует два отличия от синхронной службы регистрации.  
  
- Если вы являетесь Автозагрузка пакета, необходимо добавить <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> BackgroundLoad значение для атрибута. Дополнительные сведения о Автозагрузка пакетов VSPackage, см. в разделе [Загрузка пакетов VSPackage](../extensibility/loading-vspackages.md).  
  
- Необходимо добавить **AllowsBackgroundLoading = true** поле <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>. Дополнительные сведения о PackageRegistrationAttribute, см. в разделе [регистрация и Отмена регистрации пакетов VSPackage](../extensibility/registering-and-unregistering-vspackages.md).  
  
  Ниже приведен пример AsyncPackage с регистрацию асинхронная служба::  
  
```csharp  
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]  
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]   
[Guid(TestAsyncPackage.PackageGuidString)]  
public sealed class TestAsyncPackage : AsyncPackage  
{. . . }  
```  
  
## <a name="adding-a-service"></a>Добавление службы  
  
1.  В TestAsyncPackage.cs, удалите `Initialize()` метод и переопределение `InitializeAsync()` метод. Добавьте службу и метод обратного вызова для создания служб. Вот пример асинхронной инициализатора, добавление службы:  
  
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
  
1.  Мы покажем это в инициализаторе, но вы можете получить службу в любом месте вы хотите использовать службу.  
  
    ```csharp  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await writer.WriteLineAsync(<userpath>), "this is a test");  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
     Не забудьте изменить  *\<userpath >* имя файла и путь, который лучше всего подходит на вашем компьютере!  
  
2.  Постройте и запустите код. Когда появится в экспериментальном экземпляре Visual Studio, откройте решение. В результате AsyncPackage для автозагрузки. При запуске инициализатора следует найти файл в указанном расположении.  
  
## <a name="using-an-asynchronous-service-in-a-command-handler"></a>С помощью асинхронной службы в обработчике команд  
 Вот пример того, как использовать службу асинхронной команды меню. Можно использовать для использования службы в других-асинхронных методов, приведенных здесь.  
  
1.  Добавьте команду меню в проект. (В **обозревателе решений**, выберите узел проекта, щелкните правой кнопкой мыши и выберите **добавить / новый элемент / расширяемость / настраиваемые команды**.) Имя командного файла **TestAsyncCommand.cs.**  
  
2.  Шаблон пользовательской команды повторно добавляет `Initialize()` метод в файл TestAsyncPackage.cs для инициализации команды. В метод Initialize() Скопируйте строку, которая инициализирует команды. Он должен выглядеть так:  
  
    ```  
    TestAsyncCommand.Initialize(this);  
    ```  
  
     Переместить эту строку, чтобы `InitializeAsync()` метод в файле AsyncPackageForService.cs. Так как это в асинхронную инициализацию, необходимо переключиться на основной поток до инициализации команды с помощью <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Теперь он должен выглядеть следующим образом:  
  
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
  
4.  Найдите в файле TestAsyncCommand.cs `MenuItemCallback()` метод. Удалите тело метода.  
  
5.  Добавьте инструкцию using:  
  
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
  
8.  Постройте решение и запустите отладку. Когда Откроется экспериментальный экземпляр Visual Studio, перейдите к **средства** меню и найти **вызова TestAsyncCommand** пункта меню. Если щелкнуть его, TextWriterService Записывает указанный файл. (Не нужно открыть решение, так как при вызове команды также приводит к загрузке пакета.)  
  
## <a name="see-also"></a>См. также  
 [Использование и предоставление служб](../extensibility/using-and-providing-services.md)

