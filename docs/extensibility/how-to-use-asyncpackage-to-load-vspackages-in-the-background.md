---
title: "Практическое руководство: использование AsyncPackage для загрузки пакетов VSPackages в фоновом режиме | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: 8
ms.author: "gregvanl"
caps.handback.revision: 8
---
# Практическое руководство: использование AsyncPackage для загрузки пакетов VSPackages в фоновом режиме
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Загрузка и инициализировать пакет VS может привести к дискового ввода\-вывода. Если таких операций ввода\-вывода происходит в потоке пользовательского интерфейса, он может привести к проблемам скорости реагирования. Чтобы решить эту проблему, представила Visual Studio 2015 <xref:Microsoft.VisualStudio.Shell.AsyncPackage> класс, который позволяет загрузка пакета в фоновом потоке.  
  
## Создание AsyncPackage  
 Сначала нужно создать проект VSIX \(**файл \/ Создание \/ Project или Visual C\# и расширяемости и проект VSIX**\) и добавление в проект VSPackage \(щелкните правой кнопкой мыши проект и **Добавить новый элемент или C\# элемента и расширяемости и Visual Studio пакета**\). Затем можно создавать службы и добавьте эти службы в пакет.  
  
1.  Наследовать из пакета <xref:Microsoft.VisualStudio.Shell.AsyncPackage>.  
  
2.  Если нужно предоставить службы которого запрос может вызвать пакет для загрузки:  
  
     Для указания в Visual Studio, пакета является безопасным для загрузки в фоновом режиме и согласиться на это поведение вашей <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> следует задать **AllowsBackgroundLoading** значение true в конструктор атрибута.  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
    ```  
  
     Чтобы указать Visual Studio, что это безопасно для создания экземпляра службы в фоновом потоке, необходимо задать <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> значение true в <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> конструктора.  
  
    ```c#  
    [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
    ```  
  
3.  Если загружается через контексты пользовательского интерфейса, то следует указать **PackageAutoLoadFlags.BackgroundLoad** для <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> или значением \(0x2\) в флаги записывается как значение записи автоматически загружать ваш пакет.  
  
    ```c#  
    [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
    ```  
  
4.  При наличии инициализации асинхронной работы, необходимо переопределить <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>. Удалить **Initialize\(\)** метод, предоставленный шаблоном VSIX. \( **Initialize\(\)** метод в **AsyncPackage** запечатан\). Можно использовать любой из <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> методы для добавления асинхронные службы в пакет.  
  
     Примечание: Для вызова **базовый. InitializeAsync\(\)**, можно изменить исходный код для:  
  
    ```c#  
    await base.InitializeAsync(cancellationToken, progress);  
    ```  
  
5.  Необходимо соблюдать осторожность не создает удаленный вызов процедур \(удалите вызов процедуры\) из асинхронной инициализации кода \(в **InitializeAsync**\). Это может произойти при вызове <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> прямо или косвенно.  Когда требуются загружает синхронизации, блокирует поток пользовательского интерфейса с помощью <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>. Модель блокировки по умолчанию отключает RPC. Это означает, что при попытке использовать RPC из асинхронных задач будет взаимоблокировка Если поток пользовательского интерфейса является сам ожидание пакета для загрузки. Общие альтернативой является маршалинг код, чтобы поток пользовательского интерфейса, при необходимости, с помощью примерно **Joinable фабрики задач**<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> или другой механизм, который не использует RPC.  НЕ используйте **ThreadHelper.Generic.Invoke** или обычно блокирует вызывающий поток ожидает получения в поток пользовательского интерфейса.  
  
     Примечание: Не следует использовать **GetService** или **QueryService** в ваш **InitializeAsync** метод. Если их использовать, необходимо сначала переключиться в поток пользовательского интерфейса. Альтернативой является использование <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> из своей **AsyncPackage** \(путем приведения его к <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>.\)  
  
 C\#: Создание AsyncPackage:  
  
```c#  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]       
[ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]   
public sealed class TestPackage : AsyncPackage   
{   
    protected override Task InitializeAsync(System.Threading.CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)   
    {               
        this.AddService(typeof(SMyTestService), CreateService, true);   
        return Task.FromResult<object>(null);   
    }   
}  
```  
  
## Преобразовать существующие VSPackage AsyncPackage  
 Большая часть работы по совпадает с создания нового **AsyncPackage**. Необходимо выполнить следующие шаги с 1 по 5 выше. Необходимо также выполнить дополнительное внимание на следующее:  
  
1.  Не забудьте удалить **инициализации** переопределение имеется в пакете.  
  
2.  Избежать взаимоблокировок: может быть скрыт RPC в коде, который теперь происходит в фоновом потоке. Необходимо убедиться, что при создании RPC \(например **GetService**\), необходимо либо \(1\) переключиться в основной поток, или \(2\) используйте асинхронную версию API, если он существует \(например **GetServiceAsync**\).  
  
3.  Не переключайтесь между потоками слишком часто. Пытаться локализировать работы, могут выполняться в фоновом потоке. Это уменьшает время загрузки.  
  
## Запрос служб из AsyncPackage  
 **AsyncPackage** может или не может загрузить асинхронно в зависимости от вызывающего объекта. Например,  
  
-   Если вызывающий объект вызывается **GetService** или **QueryService** \(оба синхронного API\) или  
  
-   Если вызывающий объект вызывается **IVsShell::LoadPackage** \(или **IVsShell5::LoadPackageWithContext**\) или  
  
-   Загрузка инициируется контекста пользовательского интерфейса, но не указан, механизм контекста пользовательского интерфейса можно при асинхронной загрузки  
  
 затем пакет будет загружать синхронно.  
  
 Обратите внимание, что пакет по\-прежнему возможности \(на стадии его инициализации асинхронной\) для работы из потока пользовательского интерфейса, хотя поток пользовательского интерфейса будет заблокирован для завершения этой работы. Если он использует **IAsyncServiceProvider** для асинхронного запроса для службы, затем загрузки и инициализации выполняется асинхронно при условии, что они не блокировали непосредственно на объект результирующей задачи.  
  
 C\#: Как асинхронный запрос службы:  
  
```c#  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```