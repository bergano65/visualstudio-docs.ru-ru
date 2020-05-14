---
title: Как поставить услугу Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60cae5e8048a0234114e1f9e7d97728e26ee40f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710769"
---
# <a name="how-to-provide-a-service"></a>Как: Предоставить услугу
VSPackage может предоставлять услуги, которые могут использовать другие VSPackages. Чтобы предоставить услугу, VSPackage должен зарегистрировать услугу в Visual Studio и добавить услугу.

 Класс <xref:Microsoft.VisualStudio.Shell.Package> реализует и <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> <xref:System.ComponentModel.Design.IServiceContainer>. <xref:System.ComponentModel.Design.IServiceContainer>содержит методы обратного вызова, которые предоставляют услуги по требованию.

 Для получения дополнительной информации об [услугах](../extensibility/internals/service-essentials.md) см.

> [!NOTE]
> Когда VSPackage вот-вот будет выгружен, Visual Studio ждет, пока все запросы на услуги, которые предоставляет VSPackage, будут доставлены. Он не допускает новых запросов на эти услуги. Не следует явно вызывать <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> метод отмены службы при разгрузке.

## <a name="implement-a-service"></a>Внедрение службы

1. Создайте проект VSIX **(Файл** > **новый** > **проект** > Visual C**е** > **Расширяемость** > **VSIX проекта**).

2. Добавьте в проект VSPackage. Выберите узла проекта в **Solution Explorer** и нажмите **Добавить** > **новый элемент** > **Visual C' Элементы** > **Расширяемый** > **Визуальный Studio пакет**.

3. Для реализации службы необходимо создать три типа:

   - Интерфейс, описывающий службу. Многие из этих интерфейсов пусты, то есть у них нет методов.

   - Интерфейс, описывающий интерфейс службы. Этот интерфейс включает в себя методы, которые должны быть реализованы.

   - Класс, который реализует как службу, так и интерфейс службы.

     В следующем примере показана базовая реализация трех типов. Конструктор класса услуг должен установить поставщика услуг.

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

### <a name="register-a-service"></a>Регистрация услуги

1. Чтобы зарегистрировать услугу, <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> добавьте в VSPackage, который предоставляет услугу. Например:

    ```csharp
    [ProvideService(typeof(SMyService))]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [Guid(VSPackage1.PackageGuidString)]
    public sealed class VSPackage1 : Package
    {. . . }
    ```

     Этот атрибут `SMyService` регистрируется в Visual Studio.

    > [!NOTE]
    > Чтобы зарегистрировать службу, которая заменяет другую <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>службу с тем же именем, используйте . Обратите внимание, что допускается только одно переопределение службы.

### <a name="add-a-service"></a>Добавление службы

1. В инициализаторе VSPackage добавьте службу и добавьте метод обратного вызова для создания служб. Вот изменение, чтобы сделать в <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> метод:

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);
    . . .
    }
    ```

2. Реализация метода обратного отработки, который должен создать и вернуть службу, или свернуть, если она не может быть создана.

    ```csharp
    private object CreateService(IServiceContainer container, Type serviceType)
    {
        if (typeof(SMyService) == serviceType)
            return new MyService(this);
        return null;
    }
    ```

    > [!NOTE]
    > Visual Studio может отклонить запрос на предоставление услуги. Он делает это, если другой VSPackage уже предоставляет услугу.

3. Теперь вы можете получить услугу и использовать ее методы. Приведенный ниже пример показывает использование службы в инициаторе, но вы можете получить услугу в любом месте, где вы хотите воспользоваться услугой.

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

     Значение `helloString` должно быть "Привет".

## <a name="see-also"></a>См. также
- [Как: Получить услугу](../extensibility/how-to-get-a-service.md)
- [Использование и предоставление услуг](../extensibility/using-and-providing-services.md)
- [Основные услуги](../extensibility/internals/service-essentials.md)
