---
title: "Как: доступ к службе | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 1679fe1834b5d6246194ee4f9b3e24d6d9c09540
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="how-to-get-a-service"></a>Как: доступ к службе
Часто требуется получить службы Visual Studio для доступа к другой функции. Как правило служба Visual Studio предоставляет один или несколько интерфейсов, которые можно использовать. Большинство служб можно получить из пакета VSPackage.  
  
 Любой пакет VSPackage, который является производным от <xref:Microsoft.VisualStudio.Shell.Package> и который был размещен правильно можно задать для любой глобальной службы. Так как пакет класс реализует интерфейс <xref:System.IServiceProvider>, любой пакет VSPackage, который является производным из пакета также является поставщиком службы.  
  
 При загрузке Visual Studio <xref:Microsoft.VisualStudio.Shell.Package>, он передает <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> объект <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> метод во время инициализации. Это называется *размещение* VSPackage. Класс пакета обертывает этот поставщик услуг и предоставляет <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> метод для получения служб.  
  
## <a name="getting-a-service-from-an-initialized-vspackage"></a>Получение службы из инициализированный VSPackage  
  
1.  Все расширения Visual Studio начинается с проект развертывания VSIX, который будет содержать средств расширения. Создание [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проект VSIX с именем `GetServiceExtension`. Шаблон проекта VSIX в можно найти **новый проект** диалогового окна в разделе **Visual C# / Extensibility**.  
  
2.  Теперь добавьте пользовательскую команду шаблон элемента с именем **GetServiceCommand**. В **Добавление нового элемента** диалоговое окно, перейдите на **Visual C# / Extensibility** и выберите **настраиваемой команды**. В **имя** в нижней части окна, измените имя файла команд для **GetServiceCommand.cs**. Дополнительные сведения о том, как создать настраиваемую команду [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
3.  В GetServiceCommand.cs удалите текст метода MenuItemCommand и добавьте следующий код:  
  
    ```csharp  
    IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (activityLog == null) return;  
    System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
    ```  
  
     Этот код получает службу SVsActivityLog и приводит его к <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> интерфейс, который может использоваться для записи в журнал действий. Пример см. в разделе [как: использование журнала действий](../extensibility/how-to-use-the-activity-log.md).  
  
4.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.  
  
5.  В меню "Сервис" экспериментальный экземпляр найти **GetServiceCommand вызова** кнопки. При нажатии этой кнопки появится окно сообщения об ошибке **найти службу журнала действий.**  
  
## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Получение службы из контейнера средство окна или элемента управления  
 Иногда может потребоваться доступ к службе из окна инструментов или контейнер, в котором не размещен, иначе размещения у поставщика услуг, не знает о службу, которую вы хотите управлять. Например может потребоваться запись в журнал действий в элементе управления.  
  
 Статический <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> способ полагается на поставщик услуг кэширования, который инициализируется при первом VSPackage любой производный от <xref:Microsoft.VisualStudio.Shell.Package> размещении.  
  
 Поскольку VSPackage конструктор вызывается перед размещен пакет VSPackage, глобальные службы обычно недоступны из конструктора VSPackage. В разделе [как: Устранение неполадок служб](../extensibility/how-to-troubleshoot-services.md) для решения этой проблемы.  
  
 Ниже приведен пример способа получения службы в окно инструментов или другого элемента не VSPackage.  
  
```csharp  
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
## <a name="getting-a-service-from-the-dte-object"></a>Получение службы из объекта DTE  
 Можно также получить службы от <xref:EnvDTE.DTEClass> объекта. Тем не менее, необходимо получить объект DTE как служба с VSPackage или путем вызова статического <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> метод.  
  
 Реализует объект DTE <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>, который можно использовать для запроса службы с помощью <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>.  
  
 Вот как доступ к службе из объекта DTE.  
  
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
 [Как: обслуживать](../extensibility/how-to-provide-a-service.md)   
 [Использование и предоставления услуг](../extensibility/using-and-providing-services.md)   
 [Основные компоненты службы](../extensibility/internals/service-essentials.md)
