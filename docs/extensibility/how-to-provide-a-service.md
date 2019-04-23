---
title: Практическое руководство. Предоставляет службу | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40217c1cfcc2c7ae946e36aadb7a251436023b0a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60078633"
---
# <a name="how-to-provide-a-service"></a>Практическое руководство. Предоставляет службу
VSPackage может предоставлять службы, которые можно использовать в других пакетов VSPackage. Для предоставления службы, VSPackage должен зарегистрировать службу с помощью Visual Studio и добавить службу.

 <xref:Microsoft.VisualStudio.Shell.Package> Класс реализует оба <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> и <xref:System.ComponentModel.Design.IServiceContainer>. <xref:System.ComponentModel.Design.IServiceContainer> содержит методы обратного вызова, которые предоставляют службы по запросу.

 Дополнительные сведения о службах см. в разделе [службы essentials](../extensibility/internals/service-essentials.md) .

> [!NOTE]
>  Когда готов к выгрузке VSPackage, Visual Studio ожидает, пока не будут доставлены все запросы для служб, предоставляемых VSPackage. Он не поддерживает новые запросы для этих служб. Не следует явно вызывать <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> метод отозвать службы при выгрузке.

## <a name="implement-a-service"></a>Реализация службы

1. Создайте проект VSIX (**файл** > **New** > **проекта** > **Visual C#**  >  **Расширяемости** > **проект VSIX**).

2. Добавьте в проект VSPackage. Выберите узел проекта в **обозревателе решений** и нажмите кнопку **добавить** > **новый элемент** > **элементы Visual C#**  >  **Расширяемости** > **пакет Visual Studio**.

3. Чтобы реализовать службу, необходимо создать три типа:

   - Интерфейс, который описывает службу. Многие из этих интерфейсов пусты, то есть они имеют без методов.

   - Интерфейс, который описывает интерфейс службы. Этот интерфейс содержит методы, которые должны быть реализованы.

   - Класс, реализующий интерфейс службы и службы.

     Следующий пример показывает базовую реализацию из трех типов. Конструктор класса службы необходимо задать поставщик услуг.

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

### <a name="register-a-service"></a>Регистрация службы

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

### <a name="add-a-service"></a>Добавление службы

1. В инициализаторе VSPackage добавьте службу и добавьте метод обратного вызова для создания служб. Вот, чтобы внести изменения <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> метод:

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);
    . . .
    }
    ```

2. Реализуйте метод обратного вызова, который следует создать и вернуть служба или значение null, если не может быть создан.

    ```csharp
    private object CreateService(IServiceContainer container, Type serviceType)
    {
        if (typeof(SMyService) == serviceType)
            return new MyService(this);
        return null;
    }
    ```

    > [!NOTE]
    >  Visual Studio может отклонить запрос для предоставления службы. Она делает это, если уже в другом пакете VSPackage предоставляет службу.

3. Теперь можно получить службу и использовать его методы. В приведенном ниже примере показано использование службы в инициализатор, но вы можете получить службу в любом месте вы хотите использовать службу.

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);

        MyService myService = (MyService) this.GetService(typeof(SMyService));
        myService.Hello();
        string helloString = myService.Goodbye();

        base.Initialize();
    }
    ```

     Значение `helloString` должно быть «Hello».

## <a name="see-also"></a>См. также
- [Практическое руководство. Получение службы](../extensibility/how-to-get-a-service.md)
- [Использование и предоставление сервисов](../extensibility/using-and-providing-services.md)
- [Основные компоненты службы](../extensibility/internals/service-essentials.md)
