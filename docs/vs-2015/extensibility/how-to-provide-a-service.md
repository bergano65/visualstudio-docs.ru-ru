---
title: Руководство. предоставление службы | Документация Майкрософт
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
ms.openlocfilehash: 565a8a91797c826b6419dc5a8488d7d3baf9cddc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842720"
---
# <a name="how-to-provide-a-service"></a>Практическое руководство. Предоставление службы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Пакет VSPackage может предоставлять службы, которые могут использоваться другими пакетами VSPackage. Для предоставления службы пакет VSPackage должен зарегистрировать службу в Visual Studio и добавить службу.  
  
 <xref:Microsoft.VisualStudio.Shell.Package>Класс реализует <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> и <xref:System.ComponentModel.Design.IServiceContainer> . <xref:System.ComponentModel.Design.IServiceContainer> содержит методы обратного вызова, предоставляющие службы по запросу.  
  
 Дополнительные сведения о службах см. в разделе [Service Essentials](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
> Когда пакет VSPackage собирается выгружаться, Visual Studio ждет, пока не будут доставлены все запросы к службам, предоставляемым пакетом VSPackage. Он не разрешает новые запросы для этих служб. Не следует явно вызывать <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> метод для отзыва службы при выгрузке.  
  
#### <a name="implementing-a-service"></a>Реализация службы  
  
1. Создайте проект VSIX (**File/New/Project/Visual C#/расширяемости/VSIX Project**).  
  
2. Добавьте VSPackage в проект. Выберите узел проекта в **Обозреватель решений** и щелкните **Добавить/создать элемент/Visual C# элементы/Расширяемость/пакет Visual Studio**.  
  
3. Чтобы реализовать службу, необходимо создать три типа:  
  
   - Интерфейс, описывающий службу. Многие из этих интерфейсов пусты, т. е. у них нет методов.  
  
   - Интерфейс, описывающий интерфейс службы. Этот интерфейс включает методы, которые должны быть реализованы.  
  
   - Класс, реализующий как службу, так и интерфейс службы.  
  
     В следующем примере показана базовая реализация трех типов. Конструктор класса службы должен задать поставщик службы.  
  
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
  
1. Чтобы зарегистрировать службу, добавьте в <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> VSPackage, предоставляющий службу. Например:  
  
    ```csharp  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     Этот атрибут регистрируется `SMyService` в Visual Studio.  
  
    > [!NOTE]
    > Чтобы зарегистрировать службу, заменяющую другую службу с тем же именем, используйте <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> . Обратите внимание, что разрешено только одно переопределение службы.  
  
### <a name="adding-a-service"></a>Добавление службы  
  
1. 1.  В инициализаторе VSPackage добавьте службу и добавьте метод обратного вызова для создания служб. Ниже приведено изменение <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> метода:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2. Реализуйте метод обратного вызова, который должен создавать и возвращать службу, или значение null, если ее нельзя создать.  
  
    ```  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    > Visual Studio может отклонить запрос на предоставление службы. Это происходит, если служба уже имеется в другом пакете VSPackage.  
  
3. Теперь вы можете получить службу и использовать ее методы. Мы покажем это в инициализаторе, но вы можете получить службу в любом месте, где вы хотите использовать службу.  
  
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
  
     Значение `helloString` должно быть "Hello".  
  
## <a name="see-also"></a>См. также:  
 [Руководство. Получение службы](../extensibility/how-to-get-a-service.md)   
 [Использование и предоставление служб](../extensibility/using-and-providing-services.md)   
 [Основные компоненты службы](../extensibility/internals/service-essentials.md)
