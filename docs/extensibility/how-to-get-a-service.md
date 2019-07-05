---
title: Практическое руководство. Доступ к службе | Документация Майкрософт
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3da08f41566e5b6d2a501a9e020d589b85988016
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351937"
---
# <a name="how-to-get-a-service"></a>Практическое руководство. Получение службы

Часто требуется получить службы Visual Studio для доступа к другой функции. Как правило службы Visual Studio предоставляет один или несколько интерфейсов, которые можно использовать. Большинство служб можно получить из VSPackage.

Любой пакет VSPackage, который является производным от <xref:Microsoft.VisualStudio.Shell.Package> и, правильно размещения может запросить любой глобальной службы. Так как `Package` класс реализует <xref:System.IServiceProvider>, любой пакет VSPackage, который является производным от `Package` также является поставщиком службы.

Когда Visual Studio загружает <xref:Microsoft.VisualStudio.Shell.Package>, он передает <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> объект <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> метод во время инициализации. Это называется *расположения* VSPackage. `Package` Класс создает оболочку для этого поставщика службы и обеспечивает <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> метод для получения служб.

## <a name="getting-a-service-from-an-initialized-vspackage"></a>Получение службы из инициализированного VSPackage

1. Все расширения Visual Studio начинается с развертывания проект VSIX, который будет содержать средств расширения. Создание [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проект VSIX с именем `GetServiceExtension`. Вы найдете шаблон проекта VSIX в **новый проект** диалоговое окно, выполняя поиск «vsix».

2. Теперь Добавление пользовательской команды шаблона элемента с именем **GetServiceCommand**. В **Добавление нового элемента** диалоговое окно, перейдите к **Visual C#**  > **расширяемости** и выберите **настраиваемой команды**. В **имя** в нижней части окна, измените имя командного файла для *GetServiceCommand.cs*. Дополнительные сведения о том, как создать пользовательскую команду [создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)

3. В *GetServiceCommand.cs*, удалите основную часть `MenuItemCommand` метод и добавьте следующий код:

   ```csharp
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
   if (activityLog == null) return;
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");

   ```

    Этот код получает службу SVsActivityLog и приводит его к <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> интерфейс, который может использоваться для записи в журнал действий. Пример см. в статье [Практическое руководство. Использование журнала действий](../extensibility/how-to-use-the-activity-log.md).

4. Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.

5. На **средства** найти меню экспериментального экземпляра **вызова GetServiceCommand** кнопки. Если щелкнуть эту кнопку, вы должны увидеть окно сообщения с текстом **найти службу журнала действий.**

## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Получение службы из контейнера средство окна или элемента управления

Иногда может потребоваться доступ к службе из окна инструментов или контейнер, который не был помещен в узел, в противном случае размещения с поставщиком услуг, не знает о службу, которую вы хотите управлять. Например может потребоваться запись в журнале действий в элементе управления.

Статический <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> метод полагается на поставщик кэшированных служб, который инициализируется первый раз, любой пакет VSPackage на основе <xref:Microsoft.VisualStudio.Shell.Package> помещен в узел.

Поскольку VSPackage конструктор вызывается в том случае, прежде чем поместить VSPackage, глобальных служб обычно недоступен из конструктора VSPackage. См. практическое руководство по [ Устранение неполадок в службах](../extensibility/how-to-troubleshoot-services.md) решение этой проблемы.

Ниже приведен пример способа для получения службы в окно инструментов или другого элемента не VSPackage.

```csharp
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="getting-a-service-from-the-dte-object"></a>Получение службы из объекта DTE

Также можно получить службы из <xref:EnvDTE.DTEClass> объекта. Тем не менее, необходимо получить объект DTE как услуга из VSPackage или путем вызова статического <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> метод.

Реализует объект DTE <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>, который можно использовать для запроса службы с помощью <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>.

Вот как можно получить службы из объекта DTE.

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

- [Практическое руководство. Предоставляет службу](../extensibility/how-to-provide-a-service.md)
- [Использование и предоставление сервисов](../extensibility/using-and-providing-services.md)
- [Основные компоненты службы](../extensibility/internals/service-essentials.md)