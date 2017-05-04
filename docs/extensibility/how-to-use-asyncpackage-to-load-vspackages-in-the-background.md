---
title: "Как: используется для загрузки пакетов VSPackage в фоновом режиме AsyncPackage | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: 8
ms.author: gregvanl
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: c9df048a49580f3526b48e29041ef3758722ed27
ms.openlocfilehash: bcfdf6991c12affc1000ace72b16f97be9de469a
ms.lasthandoff: 05/03/2017

---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Как: использовать AsyncPackage для загрузки пакетов VSPackage в фоновом режиме
Загрузка и инициализация пакета VS может привести к дискового ввода-вывода. Если таких операций ввода-вывода происходит в потоке пользовательского интерфейса, он может привести к проблемам скорости реагирования. Для решения этой проблемы в Visual Studio 2015 появился < xref:Microsoft.VisualStudio.Shell.AsyncPackage > класс, который позволяет пакета загрузку в фоновом потоке.  
  
## <a name="creating-an-asyncpackage"></a>Создание AsyncPackage  
 Сначала нужно создать проект VSIX (**файл / создать / Project / Visual C# / расширяемости / проект VSIX**) и добавление в проект VSPackage (щелкните проект правой кнопкой мыши и **добавить новый элемент / C# элемента или расширяемость/Visual Studio Package**). Затем можно создать служб и добавить эти службы в пакет.  
  
1.  Пакет наследуйте от < xref:Microsoft.VisualStudio.Shell.AsyncPackage >.  
  
2.  Если вы указываете которого запрос может привести к пакету, подлежащему загрузке службы:  
  
     Для указания в Visual Studio, пакет может безопасно фоновую загрузку и согласиться на это поведение, следует установить < xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute > **AllowsBackgroundLoading** значение true в конструктор атрибута.  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
    ```  
  
     Чтобы указать Visual Studio, можно безопасно для создания экземпляра службы в фоновом потоке, следует установить свойство < xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A > значение true в конструкторе < xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute >.  
  
    ```c#  
    [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
    ```  
  
3.  При загрузке через контексты пользовательского интерфейса, а затем следует указать **PackageAutoLoadFlags.BackgroundLoad** для < xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute > или значение (0x2) в флаги записывается как значение автоматически загружать записи пакета.  
  
    ```c#  
    [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
    ```  
  
4.  При наличии работ для асинхронной инициализации, должны переопределять < xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A >. Удалить **Initialize()** метода, предоставляемого шаблоном VSIX. ( **Initialize()** метод в **AsyncPackage** является запечатанным). Можно использовать любой из методов < xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A > для добавления асинхронной служб в пакет.  
  
     Примечание: Для вызова **базового. InitializeAsync()**, можно изменить исходный код для:  
  
    ```c#  
    await base.InitializeAsync(cancellationToken, progress);  
    ```  
  
5.  Вы должны уделить особое внимание делает вызовов RPC (удаленный вызов процедуры) из асинхронной инициализации кода (в **InitializeAsync**). Это может произойти при вызове < xref:Microsoft.VisualStudio.Shell.Package.GetService%2A > прямо или косвенно.  При синхронизации загружает требуются, поток пользовательского интерфейса будет блокировать < xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory >. Модель блокировки по умолчанию отключает RPC. Это означает, что при попытке использовать RPC из асинхронных задач будет взаимоблокировка Если поток пользовательского интерфейса — Ожидание для загрузки пакета. Общие альтернативой состоит в маршалинге кода в поток пользовательского интерфейса, при необходимости, с помощью примерно **Joinable фабрики задач**элемента < xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A > или другой механизм, который не использует RPC.  НЕ используйте **ThreadHelper.Generic.Invoke** или обычно блокирует вызывающий поток ожидает получить в поток пользовательского интерфейса.  
  
     Примечание: Следует избегать использования **GetService** или **QueryService** в ваш **InitializeAsync** метод. Если требуется использовать их, необходимо сначала нужно переключиться на поток пользовательского интерфейса. Альтернативой является использование < xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A > из вашей **AsyncPackage** (путем приведения его к < xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider >.)  
  
 C#: Создайте AsyncPackage:  
  
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
  
## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Преобразование существующего пакета VSPackage в AsyncPackage  
 Большинство изменений, совпадает со значением создания нового **AsyncPackage**. Необходимо выполнить шаги 1 – 5 выше. Необходимо также выполнить дополнительное внимание на следующее:  
  
1.  Не забудьте удалить **инициализировать** переопределения, заданные в пакете.  
  
2.  Избежать взаимоблокировок: может быть скрытым удаленных вызовов процедур в коде, который теперь происходит в фоновом потоке. Необходимо убедиться, что при создании удаленного вызова Процедуры (например **GetService**), необходимо или (1) переключиться в основной поток, или (2) используйте асинхронную версию API, если он существует (например **GetServiceAsync**).  
  
3.  Не переключает потоки слишком часто. Повторите для локализации работы, могут выполняться в фоновом потоке. Это уменьшает время загрузки.  
  
## <a name="querying-services-from-asyncpackage"></a>Выполняется запрос служб из AsyncPackage  
 **AsyncPackage** может или не может загрузить асинхронно в зависимости от вызывающего объекта. Например,  
  
-   Если вызывающий объект вызывается **GetService** или **QueryService** (оба синхронного API) или  
  
-   Если вызывающий объект вызывается **IVsShell::LoadPackage** (или **IVsShell5::LoadPackageWithContext**) или  
  
-   Нагрузки инициируется контекста пользовательского интерфейса, но вы не указали том, что механизм контекста пользовательского интерфейса можно загрузить можно асинхронно  
  
 затем пакет будет загружаться синхронно.  
  
 Обратите внимание, что ваш пакет по-прежнему возможности (на стадии его инициализации асинхронного) для выполнения работы вне потока пользовательского интерфейса на то, что поток пользовательского интерфейса будет заблокирован для выполнения этой работы. Если он использует **IAsyncServiceProvider** для асинхронного запроса для службы, затем загрузки и инициализации выполняются асинхронно при условии, что они не блокировали сразу на объект результирующей задачи.  
  
 C#: Практическое руководство асинхронно запроса службы.  
  
```c#  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```

