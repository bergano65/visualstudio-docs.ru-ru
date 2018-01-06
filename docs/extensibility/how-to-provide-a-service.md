---
title: "Как: обслуживать | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ccc9b014a3d31fef4e3f491da394cdf1e9fb3ecb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-provide-a-service"></a>Как: обслуживать
VSPackage может предоставлять услуги, которые можно использовать в других пакетов VSPackage. Для предоставления службы, VSPackage необходимо зарегистрировать службу в Visual Studio и добавить службу.  
  
 <xref:Microsoft.VisualStudio.Shell.Package> Класс реализует оба <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> и <xref:System.ComponentModel.Design.IServiceContainer>. <xref:System.ComponentModel.Design.IServiceContainer>содержит методы обратного вызова, предоставляющих службы по запросу.  
  
 Дополнительные сведения о службах см. в разделе [Essentials службы](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
>  При выгрузке VSPackage Visual Studio ожидает, пока не будут доставлены все запросы к службам, предоставляемым VSPackage. Это позволяет новых запросов для этих служб. Не следует явным образом вызывать <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> метод отмены службы при выгрузке.  
  
#### <a name="implementing-a-service"></a>Реализация службы  
  
1.  Создайте проект VSIX (**файл > Создать > проект > Visual C# > Extensiblity > проект VSIX**).  
  
2.  Добавьте в проект VSPackage. Выберите узел проекта в **обозревателе решений** и нажмите кнопку **Добавить > новый элемент > элементы Visual C# > расширяемости > пакета Visual Studio**.  
  
3.  Чтобы реализовать службу, необходимо создать три типа:  
  
    -   Интерфейс, который описывает службу. Многие из этих интерфейсов пусты, то есть, они имеют нет методов.  
  
    -   Интерфейс, который описывает интерфейс службы. Этот интерфейс содержит методы, которые должны быть реализованы.  
  
    -   Класс, реализующий службу и интерфейс службы.  
  
     Пример очень простой реализации трех типов. Конструктор для класса службы необходимо установить поставщик услуг.  
  
    ```csharp  
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
  
### <a name="registering-a-service"></a>Регистрация службы  
  
1.  Чтобы зарегистрировать службу, добавьте <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> в пакет VSPackage, который предоставляет службу. Пример:  
  
    ```csharp  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     Регистрирует этот атрибут `SMyService` вместе с Visual Studio.  
  
    > [!NOTE]
    >  Чтобы зарегистрировать службу, которая заменяет другую службу с тем же именем, используйте <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>. Примечание допускается только один перезапись службы.  
  
### <a name="adding-a-service"></a>Добавление службы  
  
1.  В инициализаторе VSPackage добавьте службы и метод обратного вызова для создания служб. Вот внести изменение <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> метод:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2.  Реализуйте метод обратного вызова, который следует создать и возвращать службы или значение null, если не может быть создан.  
  
    ```csharp  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio может отклонить запрос для предоставления службы. Это происходит, если другой VSPackage уже предоставляет службу.  
  
3.  Теперь можно получить службу и использовать его методы. Мы покажем это в инициализаторе, однако вы можете получить службу в любом месте необходимо использовать службу.  
  
    ```csharp  
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
  
## <a name="see-also"></a>См. также  
 [Как: доступ к службе](../extensibility/how-to-get-a-service.md)   
 [Использование и предоставления услуг](../extensibility/using-and-providing-services.md)   
 [Основные компоненты службы](../extensibility/internals/service-essentials.md)
