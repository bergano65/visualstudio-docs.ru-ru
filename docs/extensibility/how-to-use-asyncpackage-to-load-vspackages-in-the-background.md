---
title: 'Как: Используйте AsyncPackage для загрузки VSPackages в фоновом режиме (ru) Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: 77690a1947f82f97c4aa12809a80ea61335d216d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710621"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Как: Используйте AsyncPackage для загрузки VSPackages в фоновом режиме
Загрузка и инициализация пакета VS может привести к ввоза вв/о диска. Если такое ввг/о происходит в потоке uI, это может привести к проблемам с отзывчивостью. Для решения этой проблемы Visual Studio <xref:Microsoft.VisualStudio.Shell.AsyncPackage> 2015 представила класс, который позволяет загрузить пакет на фоновом потоке.

## <a name="create-an-asyncpackage"></a>Создание AsyncPackage
 Вы можете начать с создания проекта VSIX **(Файл** > **Новый** > **проект** > Visual C **"** > **Расширяемость** > **VSIX проекта**) и добавление VSPackage к проекту (право нажмите на проект и **добавить** > **новый пункт** > C "**пункт** > **Расширяемый** > **Визуальный Studio Package**). Затем можно создать свои услуги и добавить эти услуги в свой пакет.

1. Выизвай тепакет из. <xref:Microsoft.VisualStudio.Shell.AsyncPackage>

2. Если вы предоставляете услуги, запрос которых может привести к загрузке пакета:

    Чтобы указать Visual Studio, что ваш пакет безопасен для <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> фоновой загрузки, и выбрать в этом поведении, необходимо установить **свойство AllowsBackgroundLoading** true в конструкторе атрибутов.

   ```csharp
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]

   ```

    Чтобы указать Visual Studio, что можно мгновенно мгновенно настроить службу на <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> фоновом потоке, следует установить свойство в конструкции. <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>

   ```csharp
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]

   ```

3. Если вы загружаете через контексты uI, то вы <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> должны указать **PackageAutoLoadFlags.BackgroundLoad** для ИЛИ значение (0x2) в флаги, написанные как значение вашего пакета автоматической загрузки входа.

   ```csharp
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]

   ```

4. Если у вас есть асинхронная работа инициализации, чтобы сделать, вы должны переопределить <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>. Удалите метод, `Initialize()` предусмотренный шаблоном VSIX. (Метод `Initialize()` в **AsyncPackage** запечатан). Вы можете использовать <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> любой из методов, чтобы добавить асинхронные услуги в свой пакет.

    ПРИМЕЧАНИЕ: Чтобы `base.InitializeAsync()`позвонить, вы можете изменить исходный код на:

   ```csharp
   await base.InitializeAsync(cancellationToken, progress);
   ```

5. Вы должны позаботиться, чтобы НЕ сделать RPCs (удаленный вызов процедуры) из вашего асинхронного кода инициализации (в **InitializeAsync**). Это может произойти, когда вы звоните <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> прямо или косвенно.  При необходимости синхронизации нагрузки поток uI будет блокировать с помощью. <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> Модель блокировки по умолчанию отражает RPCs. Это означает, что если вы попытаетесь использовать RPC из задач async, вы зайдёте в тупик, если поток uI сам ждет загрузки пакета. Общая альтернатива заключается в том, чтобы при необходимости при необходимости <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> использовать что-то вроде **Joinable Task Factory**или какой-либо другой механизм, который не использует RPC.  Не используйте **ThreadHelper.Generic.Invoke** или обычно блокируйте поток вызова, ожидающий, чтобы добраться до потока uI.

    ПРИМЕЧАНИЕ: Вы должны избегать использования **GetService** или **queryService** в вашем `InitializeAsync` методе. Если вам нужно использовать их, вам нужно будет сначала переключиться на поток uI. Альтернативой является <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> использование из **вашего AsyncPackage** (путем литья его <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>.)

   С: Создайте AsyncPackage:

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

## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Преобразование существующего VSPackage в AsyncPackage
 Большая часть работы такая же, как создание нового **AsyncPackage**. Следуйте шагам от 1 до 5 выше. Вы также должны проявлять особую осторожность со следующими рекомендациями:

1. Не забудьте `Initialize` удалить переопределение, имеваемые в вашем пакете.

2. Избегайте взаимоблокировки: в коде могут быть скрыты RPCs. которые теперь происходят на фоновом потоке. Убедитесь, что если вы делаете RPC (например, **GetService),** вам нужно либо (1) переключиться на основной поток или (2) использовать асинхронную версию API, если она существует (например, **GetServiceAsync).**

3. Не переключайтесь между потоками слишком часто. Попробуйте локализовать работу, которая может произойти в фоновом потоке, чтобы уменьшить время загрузки.

## <a name="querying-services-from-asyncpackage"></a>Услуги по запросу от AsyncPackage
 **AsyncPackage** может или не может загружаться асинхронно в зависимости от вызывающего абонента. Например,

- Если абонент называется **GetService** или **queryService** (оба синхронных AI) или

- Если абонент называется **IVsShell:LoadPackage** (или **IVsShell5:LoadPackageWithContext)** или

- Нагрузка запускается контекстом uI, но вы не указали, что механизм контекста uI может загрузить вас асинхронно

  после этого ваш пакет будет загружатьсинированно.

  Ваш пакет по-прежнему имеет возможность (на этапе асинхронной инициализации) выполнять работу с потоком uI, хотя поток uI будет заблокирован для завершения этой работы. Если абонент использует **IAsyncServiceProvider** для асинхронного запроса для вашей службы, то ваша нагрузка и инициализация будут выполнены асинхронно при условии, что они не сразу блокируют результирующую задачу объекта.

  Вопрос: Как асинхронно задать запрос службы:

```csharp
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;

IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;
```
