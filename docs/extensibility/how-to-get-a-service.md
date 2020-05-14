---
title: 'Как: Получить услугу Документы Майкрософт'
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e8e6f20eaa08d6bb7aaa0cc9e560856daa5959e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710956"
---
# <a name="how-to-get-a-service"></a>Как: Получить услугу

Часто требуется получить услуги Visual Studio для доступа к различным функциям. Как правило, служба Visual Studio предоставляет один или несколько интерфейсов, которые можно использовать. Вы можете получить большинство услуг от VSPackage.

Любой VSPackage, <xref:Microsoft.VisualStudio.Shell.Package> который происходит от и что был правильно расположен может запросить любую глобальную услугу. Поскольку `Package` класс <xref:System.IServiceProvider>реализует, любой VSPackage, который вытекает из `Package` также является поставщиком услуг.

Когда Visual Studio <xref:Microsoft.VisualStudio.Shell.Package>загружает, он передает <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> объект методу <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> во время инициализации. Это называется *siting* VSPackage. Класс `Package` обертывает этого поставщика <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> услуг и предоставляет метод получения услуг.

## <a name="getting-a-service-from-an-initialized-vspackage"></a>Получение услуги от инициализированного VSPackage

1. Каждое расширение Visual Studio начинается с проекта развертывания VSIX, который будет содержать активы расширения. Создайте [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проект VSIX под названием `GetServiceExtension`. Шаблон проекта VSIX можно найти в диалоге **нового проекта,** ища "vsix".

2. Теперь добавьте пользовательский шаблон элемента команды под названием **GetServiceCommand.** В диалоге **Добавить новый элемент** перейдите на **Visual C е** > **Extensibility** и выберите **пользовательские команды.** В поле **«Имя»** в нижней части окна измените имя файла команды на *GetServiceCommand.cs.* Для получения дополнительной информации о том, как создать пользовательскую команду, [создайте расширение с командой меню](../extensibility/creating-an-extension-with-a-menu-command.md)

3. В *GetServiceCommand.cs,* удалите `MenuItemCommand` тело метода и добавьте следующий код:

   ```csharp
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
   if (activityLog == null) return;
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");

   ```

    Этот код получает службу SVsActivityLog и <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> отбрасывает его в интерфейс, который может быть использован для записи в журнал активности. Например, [см. Как: Используйте журнал действий.](../extensibility/how-to-use-the-activity-log.md)

4. Выполните сборку решения и запустите отладку. Появляется экспериментальный экземпляр.

5. В меню **«Инструменты»** экспериментального экземпляра найдите кнопку **«Вывобните GetServiceCommand».** При нажатии на эту кнопку следует увидеть окно сообщений, в которое сказано, что **служба журнала активности находится в ней.**

## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Получение услуги из окна инструмента или контейнера управления

Иногда может потребоваться получить услугу из окна инструмента или контейнер управления, который не был расположен, или же был расположен с поставщиком услуг, который не знает об услуге, которую вы хотите. Например, можно написать в журнал активности из элемента управления.

Статический <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> метод опирается на поставщика кэшированных услуг, который инициализирован в первый раз, когда любой VSPackage, полученный из <xref:Microsoft.VisualStudio.Shell.Package> находится.

Поскольку конструктор VSPackage называется до того, как будет размещен VSPackage, глобальные службы, как правило, недоступны из нутри конструктора VSPackage. [Узнайте, как: Службы устранения неполадок](../extensibility/how-to-troubleshoot-services.md) для обхода.

Вот пример способа получения службы в окне инструмента или других элементах, не относясь к VSPackage.

```csharp
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="getting-a-service-from-the-dte-object"></a>Получение услуги с объекта DTE

Вы также можете <xref:EnvDTE.DTEClass> получить услуги от объекта. Тем не менее, вы должны получить объект DTE в качестве <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> службы от VSPackage или повызовустая статический метод.

Объект DTE <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>реализует, который можно использовать для запроса <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>службы с помощью.

Вот как получить услугу от объекта DTE.

```csharp
// Start with the DTE object, for example: 
// using EnvDTE;
// DTE dte = (DTE)GetService(typeof(DTE));

ServiceProvider sp = new ServiceProvider((Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);
if (sp != null)
{
    IVsActivityLog log = sp.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log != null)
    {
        System.Windows.Forms.MessageBox.Show("Found the activity log service.");
    }
}
```

## <a name="see-also"></a>См. также

- [Как: Предоставить услугу](../extensibility/how-to-provide-a-service.md)
- [Использование и предоставление услуг](../extensibility/using-and-providing-services.md)
- [Основные услуги](../extensibility/internals/service-essentials.md)
