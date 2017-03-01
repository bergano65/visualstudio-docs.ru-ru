---
title: "Практическое руководство: Получение службы | Документы Microsoft"
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f66c7e1f01c8d8eb69c6718314890bfb02cccc17
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-get-a-service"></a>Практическое руководство: Получение службы
Часто требуется получить службы Visual Studio для доступа к другой функции. Как правило обновления для Visual Studio предоставляет один или несколько интерфейсов, которые можно использовать. Большинство служб можно получить из VSPackage.  
  
 Любой VSPackage, который является производным от <xref:Microsoft.VisualStudio.Shell.Package>и который был размещен правильно может запросить любой глобальной службы.</xref:Microsoft.VisualStudio.Shell.Package> Поскольку класс пакета реализует <xref:System.IServiceProvider>, любой VSPackage, который является производным из пакета также является поставщиком.</xref:System.IServiceProvider>  
  
 Когда Visual Studio загружает <xref:Microsoft.VisualStudio.Shell.Package>, он передает <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>объект <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>метод во время инициализации.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> </xref:Microsoft.VisualStudio.Shell.Package> Это называется *размещение* VSPackage. Класс пакета этот поставщик услуг упаковывает и предоставляет <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>метод для получения служб.</xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>  
  
## <a name="getting-a-service-from-an-initialized-vspackage"></a>Получение службы из инициализированный VSPackage  
  
1.  Все расширения Visual Studio начинается с развертывания проект VSIX, который будет содержать средств расширения. Создание [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проект VSIX с именем `GetServiceExtension`. Можно найти шаблон проекта VSIX в **новый проект** диалоговом окне под **Visual C# и расширяемость**.  
  
2.  Теперь добавьте пользовательскую команду шаблон элемента с именем **GetServiceCommand**. В **Добавление нового элемента** диалоговое окно, последовательно выберите пункты **Visual C# и расширяемость** и выберите **настраиваемой команды**. В **имя** в нижней части окна, измените имя файла команд для **GetServiceCommand.cs**. Дополнительные сведения о создании пользовательской команды [создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
3.  В GetServiceCommand.cs удалите тело метода MenuItemCommand и добавьте следующий код:  
  
    ```c#  
    IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (activityLog == null) return;  
    System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
    ```  
  
     Этот код получает службу SVsActivityLog и приводит его к <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>интерфейс, который может использоваться для записи в журнал действий.</xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> Пример см. в разделе [Практическое руководство: использование журнала действий](../extensibility/how-to-use-the-activity-log.md).  
  
4.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.  
  
5.  В меню Сервис экспериментальный экземпляр найти **GetServiceCommand вызова** кнопки. При нажатии этой кнопки появится окно сообщения с сообщением **найти службу журнала действий.**  
  
## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Получение службы из контейнера средство окна или элемента управления  
 Иногда может потребоваться обращение к службе из окна инструментов или контейнер, в котором не размещен, иначе размещения с поставщиком услуг, не знает о службу, которую вы хотите управлять. Например можно записать в журнал активности в элементе управления.  
  
 Статический <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>метод основывается на кэшированные поставщиком, инициализируется впервые VSPackage любой производный от <xref:Microsoft.VisualStudio.Shell.Package>размещении.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>  
  
 Поскольку конструктор VSPackage вызывается, прежде чем поместить VSPackage, глобальные службы обычно недоступен из конструктора VSPackage. В разделе [как: Устранение неполадок служб](../extensibility/how-to-troubleshoot-services.md) для решения этой проблемы.  
  
 Ниже приведен пример способа получения службы в окне инструментов или другой элемент не VSPackage.  
  
```c#  
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
## <a name="getting-a-service-from-the-dte-object"></a>Получение службы из объекта DTE  
 Можно также получить службы от <xref:EnvDTE.DTEClass>объекта.</xref:EnvDTE.DTEClass> Тем не менее, необходимо получить объект DTE как служба из VSPackage или путем вызова статического <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>метод.</xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>  
  
 Реализует объект DTE <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>, который можно использовать для запроса службы с помощью <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>.</xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>  
  
 Вот как можно получить из объекта DTE службы.  
  
```c#  
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
 [Практическое руководство: предоставления службы](../extensibility/how-to-provide-a-service.md)   
 [Использование и предоставления услуг](../extensibility/using-and-providing-services.md)   
 [Основы службы](../extensibility/internals/service-essentials.md)
