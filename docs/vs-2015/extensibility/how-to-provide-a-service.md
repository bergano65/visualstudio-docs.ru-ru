---
title: Практическое руководство. Предоставляет службу | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ba007a8084355445f0404a9b0f7a2c1cee7b2005
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60108195"
---
# <a name="how-to-provide-a-service"></a>Практическое руководство. Предоставление службы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage может предоставлять службы, которые можно использовать в других пакетов VSPackage. Для предоставления службы, VSPackage должен зарегистрировать службу с помощью Visual Studio и добавить службу.  
  
 <xref:Microsoft.VisualStudio.Shell.Package> Класс реализует оба <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> и <xref:System.ComponentModel.Design.IServiceContainer>. <xref:System.ComponentModel.Design.IServiceContainer> содержит методы обратного вызова, которые предоставляют службы по запросу.  
  
 Дополнительные сведения о службах см. в разделе [основные компоненты службы](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
>  Когда готов к выгрузке VSPackage, Visual Studio ожидает, пока не будут доставлены все запросы для служб, предоставляемых VSPackage. Он не поддерживает новые запросы для этих служб. Не следует явно вызывать <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> метод отозвать службы при выгрузке.  
  
#### <a name="implementing-a-service"></a>Реализация службы  
  
1. Создайте проект VSIX (**файл / создать / проект / Visual C# / артефактам / проект VSIX**).  
  
2. Добавьте в проект VSPackage. Выберите узел проекта в **обозревателе решений** и нажмите кнопку **добавить / новый элемент / элементы Visual C# / расширяемость / пакет Visual Studio**.  
  
3. Чтобы реализовать службу, необходимо создать три типа:  
  
   - Интерфейс, который описывает службу. Многие из этих интерфейсов пусты, то есть они имеют без методов.  
  
   - Интерфейс, который описывает интерфейс службы. Этот интерфейс содержит методы, которые должны быть реализованы.  
  
   - Класс, реализующий интерфейс службы и службы.  
  
     В следующем примере простейшую реализацию из трех типов. Конструктор класса службы необходимо задать поставщик услуг.  
  
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
  
1. Чтобы зарегистрировать службу, добавьте <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> к VSPackage, который предоставляет службу. Пример:  
  
    ```csharp  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     Этот атрибут регистрирует `SMyService` с помощью Visual Studio.  
  
    > [!NOTE]
    >  Чтобы зарегистрировать службу, которая заменяет другую службу с тем же именем, используйте <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>. Примечание допускается только один перезапись службы.  
  
### <a name="adding-a-service"></a>Добавление службы  
  
1. 1.  В инициализаторе VSPackage добавьте службу и добавьте метод обратного вызова для создания служб. Вот, чтобы внести изменения <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> метод:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2. Реализуйте метод обратного вызова, который следует создать и вернуть служба или значение null, если не может быть создан.  
  
    ```  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio может отклонить запрос для предоставления службы. Она делает это, если уже в другом пакете VSPackage предоставляет службу.  
  
3. Теперь можно получить службу и использовать его методы. Мы покажем это в инициализаторе, но вы можете получить службу в любом месте вы хотите использовать службу.  
  
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
 [Практическое руководство. Получение службы](../extensibility/how-to-get-a-service.md)   
 [Использование и предоставление служб](../extensibility/using-and-providing-services.md)   
 [Основные компоненты службы](../extensibility/internals/service-essentials.md)
