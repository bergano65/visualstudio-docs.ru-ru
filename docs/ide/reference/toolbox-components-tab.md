---
title: "Панель элементов, вкладка &quot;Компоненты&quot; | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Toolbox, Components tab
ms.assetid: 332fafab-a763-4244-b388-15d1b5b5cc04
caps.latest.revision: 14
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 3a1ae20e3aca94339621546ac69bbfffd3a75ab3
ms.contentlocale: ru-ru
ms.lasthandoff: 05/30/2017

---
# <a name="toolbox-components-tab"></a>Вкладка "Компоненты", панель элементов
Отображает компоненты, которые можно добавить в конструкторы [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] и [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. В дополнение к компонентам [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)], которые входят в состав [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], таким как <xref:System.Messaging.MessageQueue> и <xref:System.Diagnostics.EventLog>, на этой вкладке можно добавить собственные или сторонние компоненты. Для получения дополнительной информации см. раздел [Практическое руководство. Управление вкладками панели элементов](http://msdn.microsoft.com/en-us/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
 Чтобы отобразить эту вкладку, в меню **Вид** выберите пункт **Панель элементов**. В **панели элементов** выберите вкладку **Компоненты**.  
  
 **BackgroundWorker**  
 Создает экземпляр компонента `System.ComponentModel.BackgroundWorker`, который может выполнять операцию в отдельном выделенном потоке.  
  
 **DirectoryEntry**  
 Создает экземпляр компонента <xref:System.DirectoryServices.DirectoryEntry>, который инкапсулирует узел или объект в иерархии Active Directory и может использоваться для взаимодействия с поставщиками служб Active Directory.  
  
 **DirectorySearcher**  
 Создает экземпляр компонента <xref:System.DirectoryServices.DirectorySearcher>, который можно использовать для выполнения запросов к Active Directory.  
  
 **ErrorProvider**  
 Создает экземпляр компонента `System.Windows.Forms.ErrorProvider`, который указывает конечному пользователю, что с элементом управления в форме связана ошибка.  
  
 **EventLog**  
 Создает экземпляр компонента <xref:System.Diagnostics.EventLog>, который можно использовать для взаимодействия с системой и пользовательскими журналами событий, включая запись событий в журнал и чтения данных журнала. Дополнительные сведения см. в разделе [Знакомство с компонентом EventLog](http://msdn.microsoft.com/en-us/a2ba4f28-4b1a-435e-99ef-51b28e21f805).  
  
 **FileSystemWatcher**  
 Создает экземпляр компонента <xref:System.IO.FileSystemWatcher>, который можно использовать для отслеживания изменений в любом каталоге или файле, к которому имеется доступ. Дополнительные сведения см. в разделе [Практическое руководство. Настройка экземпляров компонента FileSystemWatcher](http://msdn.microsoft.com/en-us/2e628234-4951-4135-8a86-28b924070d50).  
  
 **HelpProvider**  
 Создает экземпляр компонента `System.Windows.Forms.HelpProvider`, который обеспечивает для элементов управления всплывающее окно справки или окно оперативной справки.  
  
 **ImageList**  
 Создает экземпляр компонента `System.Windows.Forms.ImageList`, который предоставляет методы для управления коллекцией объектов `System.Drawing.Image`.  
  
 **MessageQueue**  
 Создает экземпляр компонента <xref:System.Messaging.MessageQueue>, который можно использовать для взаимодействия с очередями сообщений, включая чтение сообщений из очередей и запись их туда, обработка транзакций и выполнение задач администрирования очередей. Дополнительные сведения см. в разделе [Использование компонентов для обмена сообщениями](http://msdn.microsoft.com/en-us/922dbac7-26f0-4e39-b666-ccfc184793d7).  
  
 **PerformanceCounter**  
 Создает экземпляр компонента <xref:System.Diagnostics.PerformanceCounter>, который можно использовать для взаимодействия со счетчиками производительности Windows, включая создание новых категорий и экземпляров, чтения значений из счетчиков и выполнения вычислений на основе данных счетчиков. Дополнительные сведения см. в разделе [Отслеживание пороговых значений производительности](http://msdn.microsoft.com/en-us/b8b44a55-31d0-4b45-9517-8c1b1e4fdc91).  
  
 **Process**  
 Создает экземпляр компонента <xref:System.Diagnostics.Process>, который можно использовать для остановки, запуска и изменения данных, связанных с процессами в системе. Дополнительные сведения см. в разделе [Мониторинг процессов Windows и управление ими](http://msdn.microsoft.com/en-us/a86bd4c1-b92c-49a0-8f32-61d67837b45e).  
  
 **SerialPort**  
 Создает экземпляр компонента `System.IO.Ports.SerialPort`, который предоставляет средства для синхронного и управляемого событиями ввода-вывода, доступа к состоянию подключения-отключения устройства, а также для доступа к свойствам драйвера последовательного порта.  
  
 **ServiceController**  
 Создает экземпляр компонента <xref:System.ServiceProcess.ServiceController>, который можно использовать для управления существующими службами, включая запуск и остановку служб, а также передачу им команд. Дополнительные сведения см. в разделе[Мониторинг служб Windows](http://msdn.microsoft.com/en-us/4542ee3f-e052-4cb9-8726-58e9420de222).  
  
 **Таймер**  
 Создает экземпляр компонента <xref:System.Windows.Forms.Timer>, который можно использовать для добавления функций на основе времени для Windows-приложений. Дополнительную информацию см. в разделе [Компонент таймера](/dotnet/framework/winforms/controls/timer-component-windows-forms).  
  
> [!NOTE]
>  Существует также системный <xref:System.Timers.Timer>, который можно добавить на **панель элементов**. Этот компонент <xref:System.Timers.Timer> оптимизирован для серверных приложений и Windows Forms. <xref:System.Windows.Forms.Timer> лучше всего подходит для использования в формах Windows Forms.  
  
## <a name="see-also"></a>См. также  
 [Программирование с использованием компонентов](http://msdn.microsoft.com/Library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)   
 [Пошаговые руководства программирования компонентов](http://msdn.microsoft.com/Library/373cacf7-479e-4b05-991c-5cb18824e913)   
 [Панель элементов](../../ide/reference/toolbox.md)   
 [Диалоговое окно "Выбор элементов панели элементов" (Visual Studio)](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb)
