---
title: "Практическое руководство: предоставления службы | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "службы, обеспечивая"
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# Практическое руководство: предоставления службы
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPackage можно предоставлять службы, которые могут использовать другие пакеты VSPackage. Для предоставления службы, VSPackage зарегистрируйте службу с помощью Visual Studio и добавить службу.  
  
 <xref:Microsoft.VisualStudio.Shell.Package> Класс реализует <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> и <xref:System.ComponentModel.Design.IServiceContainer>.<xref:System.ComponentModel.Design.IServiceContainer> содержит методы обратного вызова, предоставляющие службы по запросу.  
  
 Дополнительные сведения о службах см. в разделе [Основы службы](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
>  При выгрузке VSPackage Visual Studio ожидает, пока будут доставлены все запросы к службам, предоставляемым VSPackage. Это позволяет новых запросов для этих служб. Не следует явным образом вызывать <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> метод отозвать службы при выгрузке.  
  
#### Реализация службы  
  
1.  Создайте проект VSIX \(**файл \/ New \/ Project или Visual C\# и Extensiblity и проект VSIX**\).  
  
2.  Добавьте в проект VSPackage. Выберите узел проекта в **обозревателе решений** и нажмите кнопку **Добавить \/ Создание элемента или элементы Visual C\# или расширения или пакета Visual Studio**.  
  
3.  Для реализации службы, необходимо создать три типа:  
  
    -   Интерфейс, который описывает службу. Многие из этих интерфейсов пусты, то есть, они имеют методы не.  
  
    -   Интерфейс, который описывает интерфейс службы. Этот интерфейс содержит методы, которые должны быть реализованы.  
  
    -   Класс, реализующий интерфейс службы и службы.  
  
     Пример очень простой реализации трех типов. Конструктор класса службы необходимо задать поставщика услуг.  
  
    ```c#  
    public class MyService : SMyService, IMyService  
    {  
        private Microsoft.VisualStudio.OLE.Interop.IServiceProvider serviceProvider;  
        private string myString;  
        public MyService(Microsoft.VisualStudio.OLE.Interop.IServiceProvider sp)  
        {  
            Trace.WriteLine(  
                   "Constructing a new instance of MyService");  
            serviceProvider = sp;  
        }  
        public void Hello()  
        {  
            myString = "hello";  
        }  
        public string Goodbye()  
        {  
           return "goodbye";  
        }  
    }  
    public interface SMyService  
    {  
    }  
    public interface IMyService  
    {  
        void Hello();  
        string Goodbye();  
    }  
  
    ```  
  
### Регистрация службы  
  
1.  Чтобы зарегистрировать службу, добавьте <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> в VSPackage, который предоставляет службу. Ниже приведен пример:  
  
    ```c#  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     Регистрирует этот атрибут `SMyService` вместе с Visual Studio.  
  
    > [!NOTE]
    >  Чтобы зарегистрировать службу, которая заменяет другой службы с тем же именем, используйте <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>. Примечание допускается только один перезапись службы.  
  
### Добавление службы  
  
1.  1.	В инициализаторе VSPackage добавьте службы и добавьте метод обратного вызова для создания служб. Вот изменение вносить <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> метод:  
  
    ```c#  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2.  Реализуйте метод обратного вызова, который следует создать и вернуть службы или значение null, если не может быть создан.  
  
    ```  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio может отклонить запрос для предоставления службы. Это выполняется, если другой VSPackage уже предоставляет службу.  
  
3.  Теперь можно получить службу и использовать его методы. Мы покажем это инициализатор, но можно получить службу в любом месте вы хотите использовать службу.  
  
    ```c#  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
  
        MyService myService = (MyService) this.GetService(typeof(SMyService));  
        myService.Hello();  
        string helloString = myService.myString;  
  
        base.Initialize();  
    }  
    ```  
  
     Значение `helloString` должно быть «Hello».  
  
## См. также  
 [Практическое руководство: Получение службы](../Topic/How%20to:%20Get%20a%20Service.md)   
 [Использование и предоставления услуг](../extensibility/using-and-providing-services.md)   
 [Основы службы](../extensibility/internals/service-essentials.md)