---
title: Практическое руководство. Использование AsyncPackage для загрузки пакетов VSPackage в фоновом режиме | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: gregvanl
ms.author: gregvanl
ms.workload:
- vssdk
ms.openlocfilehash: 8a0de1ccf4a75bb10ae120e9237ceb176a3794a1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680988"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Практическое руководство. Использование AsyncPackage для загрузки пакетов VSPackage в фоновом режиме
Загрузка и инициализация пакета VS может привести дискового ввода-вывода. В случае таких операций ввода-вывода в потоке пользовательского интерфейса, он может привести к проблемам скорости реагирования. Чтобы решить эту проблему, Visual Studio 2015 представлен <xref:Microsoft.VisualStudio.Shell.AsyncPackage> класс, который позволяет загрузка пакета в фоновом потоке.

## <a name="create-an-asyncpackage"></a>Создание AsyncPackage
 Можно начать с создания проекта VSIX (**файл** > **New** > **проекта** > **Visual C#**   >  **Расширяемости** > **проект VSIX**) и добавьте в проект VSPackage (правой кнопкой мыши проект и **добавить**  >  **Новый элемент**  >   **C# элемент** > **расширяемости**  >   **Пакет Visual Studio**). Затем можно создать свои службы и добавить эти службы в пакет.

1. Производные пакет из <xref:Microsoft.VisualStudio.Shell.AsyncPackage>.

2. Если вы предоставляете которого запрос может привести к загрузке пакета служб:

    Чтобы указать для Visual Studio, что ваш пакет безопасен для загрузки фона и согласиться на это поведение вашей <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> следует задать **AllowsBackgroundLoading** свойство в значение true в конструктор атрибута.

   ```csharp
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]

   ```

    Чтобы указать Visual Studio, что он безопасен для создания экземпляра службы в фоновом потоке, необходимо задать <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> свойство в значение true в <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> конструктор.

   ```csharp
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]

   ```

3. Если при загрузке с помощью контекстов пользовательского интерфейса, то следует указать **PackageAutoLoadFlags.BackgroundLoad** для <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> или значение (0x2) в флаги записывается как значение записи автоматически загружать пакета.

   ```csharp
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]

   ```

4. Если у вас есть работы асинхронной инициализации, следует переопределить <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>. Удалить `Initialize()` метод, предоставленный шаблоном VSIX. ( `Initialize()` Метод в **AsyncPackage** является запечатанным). Можно использовать любой из <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> методы для добавления асинхронные службы в пакет.

    ПРИМЕЧАНИЕ. Для вызова `base.InitializeAsync()`, можно изменить исходный код для:

   ```csharp
   await base.InitializeAsync(cancellationToken, progress);
   ```

5. Вы должны уделить особое внимание не вносить вызовов RPC (удаленный вызов процедуры) из асинхронной инициализации кода (в **InitializeAsync**). Это может произойти при вызове <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> прямо или косвенно.  При необходимости загружает синхронизации будет блокировать поток пользовательского интерфейса с помощью <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>. Модель блокировки по умолчанию отключает удаленный вызов процедур. Это означает, что если вы попытаетесь использовать RPC из вашей асинхронных задач, будет взаимоблокировка Если поток пользовательского интерфейса — Ожидание к загрузке пакета. Общие вариант — упаковать код в поток пользовательского интерфейса, при необходимости, например **присоединяемую фабрику задач** <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> или другой механизм, использует ли RPC.  НЕ используйте **ThreadHelper.Generic.Invoke** или обычно блокируют вызывающий поток ожидает получить в поток пользовательского интерфейса.

    ПРИМЕЧАНИЕ. Следует избегать использования **GetService** или **QueryService** в вашей `InitializeAsync` метод. Если вам нужно использовать их, необходимо сначала переключиться на поток пользовательского интерфейса. Альтернативой является использование <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> из вашей **AsyncPackage** (путем приведения его к <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>.)

   C#: Создайте AsyncPackage:

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
 Большая часть работы совпадает с создания нового **AsyncPackage**. Выполните шаги 1 – 5 выше. Также вам потребуется выполнить дополнительное внимание следующие рекомендации.

1.  Не забудьте удалить `Initialize` переопределение, имеется в пакете.

2.  Избегайте взаимоблокировок: Может быть скрыт RPC в коде. Теперь это происходить в фоновом потоке. Убедитесь, что при создании RPC (например, **GetService**), необходимо или (1) переключиться на основной поток или (2) используйте асинхронную версию метода API, если он существует (например, **GetServiceAsync**).

3.  Не переключайтесь между потоками слишком часто. Попробуйте для локализации работу, может произойти в фоновом потоке, чтобы сократить время загрузки.

## <a name="querying-services-from-asyncpackage"></a>Запрос служб из AsyncPackage
 **AsyncPackage** может или не может загрузить асинхронно в зависимости от вызывающего объекта. Например,

- Если вызывающий объект вызвать **GetService** или **QueryService** (оба синхронных API) или

- Если вызывающий объект вызвать **IVsShell::LoadPackage** (или **IVsShell5::LoadPackageWithContext**) или

- Нагрузки инициируется контекст пользовательского интерфейса, но не указан, механизм контекста пользовательского интерфейса можно вы асинхронной загрузки

  затем пакет будет загружать синхронно.

  Пакет по-прежнему имеет возможность (на стадии его инициализации асинхронной) для выполнения работы вне потока пользовательского интерфейса, на то, что в потоке пользовательского интерфейса будет заблокирован для завершения этой работы. Если вызывающий объект использует **IAsyncServiceProvider** для асинхронного запроса для службы, затем нагрузочных тестах и инициализации, выполняются асинхронно при условии, что они не блокировать немедленно, в полученном объекте задачи.

  C#: Как запросить службы асинхронно:

```csharp
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;

IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;
```
