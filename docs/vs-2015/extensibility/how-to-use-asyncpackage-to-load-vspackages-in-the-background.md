---
title: Как использовать AsyncPackage для загрузки пакетов VSPackage в фоновом режиме | Документация Майкрософт
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: 9
ms.author: gregvanl
ms.openlocfilehash: f59838913ed3f9bc6679336393f6db9181291e3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204023"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Практическое руководство. Использование AsyncPackage для загрузки пакетов VSPackage в фоновом режиме
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Загрузка и инициализация пакета VS могут привести к диску ввода-вывода. Если такие операции ввода-вывода выполняются в потоке пользовательского интерфейса, это может привести к проблемам реагирования. Чтобы устранить эту эту необходимость, в Visual Studio 2015 появился  <xref:Microsoft.VisualStudio.Shell.AsyncPackage> класс, позволяющий загружать пакеты в фоновом потоке.  
  
## <a name="creating-an-asyncpackage"></a>Создание AsyncPackage  
 Вы можете начать с создания проекта VSIX (**файл/создать/проект/Visual C#/расширяемость/VSIX проект**) и добавить пакет VSPackage в проект (щелкните правой кнопкой мыши проект и в контекстном меню выберите пункт **Добавить/создать элемент/расширяемость или пакет Visual Studio**). Затем можно создать службы и добавить эти службы в пакет.  
  
1. Создайте производный пакет от <xref:Microsoft.VisualStudio.Shell.AsyncPackage> .  
  
2. Если вы предоставляете службы, запросы которых могут привести к загрузке пакета:  
  
    Чтобы указать Visual Studio, что пакет является защищенным для фоновой загрузки и чтобы принять такое поведение, <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> необходимо установить свойство **алловсбаккграундлоадинг** в значение true в конструкторе атрибута.  
  
   ```csharp  
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
   ```  
  
    Чтобы указать Visual Studio, что для безопасного создания экземпляра службы в фоновом потоке необходимо задать <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> для свойства значение true в <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> конструкторе.  
  
   ```csharp  
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
   ```  
  
3. Если вы загружаете через контексты пользовательского интерфейса, то следует указать **паккажеаутолоадфлагс. баккграундлоад** для <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> или значение (0x2) в флагах, записанных в качестве значения записи автоматической загрузки пакета.  
  
   ```csharp  
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
   ```  
  
4. При работе с асинхронной инициализацией необходимо переопределить <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A> . Удалите метод **Initialize ()** , предоставленный шаблоном VSIX. (Метод **Initialize ()** в **AsyncPackage** запечатан). Для <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> добавления асинхронных служб в пакет можно использовать любой из методов.  
  
    Примечание. для вызова **base.Iniтиализеасинк ()** можно изменить исходный код следующим образом:  
  
   ```csharp  
   await base.InitializeAsync(cancellationToken, progress);  
   ```  
  
5. Необходимо не создавать вызовы RPC (удалить вызов процедуры) из кода асинхронной инициализации (в **инитиализеасинк**). Они могут возникать при <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> прямом или косвенном вызове.  Если требуется загрузка синхронизации, поток пользовательского интерфейса будет блокироваться с помощью <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> . Модель блокировки по умолчанию отключает вызовы RPC. Это означает, что при попытке использовать RPC из асинхронных задач вы взаимоблокируете, если поток пользовательского интерфейса ожидает загрузки пакета. В общем случае при необходимости можно выполнить упаковку кода в поток пользовательского интерфейса, используя нечто вроде **соединяемой фабрики задач** <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> или другой механизм, который не использует RPC.  НЕ используйте **среадхелпер. Generic. Invoke** или, как правило, блокируют вызывающий поток, ожидающий получения потока пользовательского интерфейса.  
  
    Примечание. следует избегать **использования функции** **QueryService** или метода **инитиализеасинк** . Если необходимо использовать их, необходимо сначала переключиться на поток пользовательского интерфейса. Альтернативой является использование <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> из **AsyncPackage** (путем приведения его к <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider> .)  
  
   C#: создание AsyncPackage:  
  
```csharp  
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
 Большая часть работы аналогична созданию нового **AsyncPackage**. Необходимо выполнить шаги с 1 по 5 выше. Кроме того, необходимо принять во внимание следующие меры.  
  
1. Не забудьте удалить переопределение **инициализации** , которое было в вашем пакете.  
  
2. Избегайте взаимоблокировок. в коде могут быть скрытые RPC, которые теперь происходят в фоновом потоке. Необходимо убедиться, что при создании RPC (например, **службы**) необходимо либо (1) переключиться на основной поток, либо (2) использовать асинхронную версию API, если таковая существует (например, **жетсервицеасинк**).  
  
3. Не переключаться между потоками слишком часто. Попробуйте локализовать работу, которая может произойти в фоновом потоке. Это сокращает время загрузки.  
  
## <a name="querying-services-from-asyncpackage"></a>Запросы к службам из AsyncPackage  
 **AsyncPackage** может быть или не загружаться асинхронно в зависимости от вызывающего объекта. Например,  
  
- Если вызывающий объект **вызвал метод** **QueryService** или (оба синхронных API) или  
  
- Если вызывающий объект вызвал **IVsShell:: LoadPackage** (или **IVsShell5:: лоадпаккажевисконтекст**) или  
  
- Загрузка активируется контекстом пользовательского интерфейса, но механизм контекста пользовательского интерфейса может загрузиться асинхронно  
  
  Затем пакет будет загружаться синхронно.  
  
  Обратите внимание, что у пакета по-прежнему есть возможность (на этапе асинхронной инициализации) для работы с потоком пользовательского интерфейса, хотя поток пользовательского интерфейса будет заблокирован для выполнения этой работы. Если вызывающий объект использует **иасинксервицепровидер** для асинхронного запроса к службе, то загрузка и инициализация будут выполняться асинхронно, предполагая, что они сразу не блокируют результирующий объект задачи.  
  
  C#: асинхронный запрос к службе:  
  
```csharp  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```
