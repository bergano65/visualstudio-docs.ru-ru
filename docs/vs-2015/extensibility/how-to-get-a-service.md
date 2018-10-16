---
title: 'Практическое: доступ к службе | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 426d0b71a23ea53a21b382ec02b8853f9ff2deb2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229688"
---
# <a name="how-to-get-a-service"></a>Практическое: Получение службы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Часто требуется получить службы Visual Studio для доступа к другой функции. Как правило службы Visual Studio предоставляет один или несколько интерфейсов, которые можно использовать. Большинство служб можно получить из VSPackage.  
  
 Любой пакет VSPackage, который является производным от <xref:Microsoft.VisualStudio.Shell.Package> и, правильно размещения может запросить любой глобальной службы. Поскольку класс пакета реализует <xref:System.IServiceProvider>, любой пакет VSPackage, который является производным от пакета также является поставщиком службы.  
  
 Когда Visual Studio загружает <xref:Microsoft.VisualStudio.Shell.Package>, он передает <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> объект <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> метод во время инициализации. Это называется *расположения* VSPackage. Класс пакета создает оболочку этого поставщика службы и предоставляет <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> метод для получения служб.  
  
## <a name="getting-a-service-from-an-initialized-vspackage"></a>Получение службы из инициализированного VSPackage  
  
1.  Все расширения Visual Studio начинается с проект развертывания VSIX, который будет содержать средств расширения. Создание [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] проект VSIX с именем `GetServiceExtension`. Вы найдете шаблон проекта VSIX в **новый проект** диалоговое окно, в разделе **Visual C# / Extensibility**.  
  
2.  Теперь Добавление пользовательской команды шаблона элемента с именем **GetServiceCommand**. В **Добавление нового элемента** диалоговое окно, перейдите к **Visual C# / Extensibility** и выберите **настраиваемой команды**. В **имя** в нижней части окна, измените имя командного файла для **GetServiceCommand.cs**. Дополнительные сведения о том, как создать пользовательскую команду [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
3.  В GetServiceCommand.cs удалить тело метода MenuItemCommand и добавьте следующий код:  
  
    ```csharp  
    IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (activityLog == null) return;  
    System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
    ```  
  
     Этот код получает службу SVsActivityLog и приводит его к <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> интерфейс, который может использоваться для записи в журнал действий. Например, см. в разделе [как: использование журнала действий](../extensibility/how-to-use-the-activity-log.md).  
  
4.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.  
  
5.  В меню "Сервис" экспериментального экземпляра, найти **вызова GetServiceCommand** кнопки. Если щелкнуть эту кнопку, вы должны увидеть окно сообщения с текстом **найти службу журнала действий.**  
  
## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Получение службы из контейнера средство окна или элемента управления  
 Иногда может потребоваться доступ к службе из окна инструментов или контейнер, который не был помещен в узел, в противном случае размещения с поставщиком услуг, не знает о службу, которую вы хотите управлять. Например может потребоваться запись в журнале действий в элементе управления.  
  
 Статический <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> метод полагается на поставщик кэшированных служб, который инициализируется первый раз, любой пакет VSPackage на основе <xref:Microsoft.VisualStudio.Shell.Package> помещен в узел.  
  
 Поскольку VSPackage конструктор вызывается в том случае, прежде чем поместить VSPackage, глобальных служб обычно недоступен из конструктора VSPackage. См. в разделе [как: Устранение неполадок служб](../extensibility/how-to-troubleshoot-services.md) решение этой проблемы.  
  
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
 [Практическое: предоставить службу](../extensibility/how-to-provide-a-service.md)   
 [Использование и предоставление служб](../extensibility/using-and-providing-services.md)   
 [Основные компоненты службы](../extensibility/internals/service-essentials.md)

