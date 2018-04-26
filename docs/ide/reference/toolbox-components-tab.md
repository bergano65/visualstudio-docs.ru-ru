---
title: Вкладка "Компоненты", панель элементов
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Toolbox, Components tab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8a05ea5b06e985a21fbe45882ccfb36bfe194034
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="toolbox-components-tab"></a>Вкладка "Компоненты", панель элементов

Отображает компоненты, которые можно добавить в конструкторы Visual Basic и C#. В дополнение к компонентам .NET Framework, которые входят в состав Visual Studio (например, <xref:System.Messaging.MessageQueue> и <xref:System.Diagnostics.EventLog>), на этой вкладке можно добавить собственные или сторонние компоненты.

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

 Создает экземпляр компонента <xref:System.Diagnostics.EventLog>, который можно использовать для взаимодействия с системой и пользовательскими журналами событий, включая запись событий в журнал и чтения данных журнала.

 **FileSystemWatcher**

 Создает экземпляр компонента <xref:System.IO.FileSystemWatcher>, который можно использовать для отслеживания изменений в любом каталоге или файле, к которому имеется доступ.

 **HelpProvider**

 Создает экземпляр компонента `System.Windows.Forms.HelpProvider`, который обеспечивает для элементов управления всплывающее окно справки или окно оперативной справки.

 **ImageList**

 Создает экземпляр компонента `System.Windows.Forms.ImageList`, который предоставляет методы для управления коллекцией объектов `System.Drawing.Image`.

 **MessageQueue**

 Создает экземпляр компонента <xref:System.Messaging.MessageQueue>, который можно использовать для взаимодействия с очередями сообщений, включая чтение сообщений из очередей и запись их туда, обработка транзакций и выполнение задач администрирования очередей.

 **PerformanceCounter**

 Создает экземпляр компонента <xref:System.Diagnostics.PerformanceCounter>, который можно использовать для взаимодействия со счетчиками производительности Windows, включая создание новых категорий и экземпляров, чтения значений из счетчиков и выполнения вычислений на основе данных счетчиков.

 **Process**

 Создает экземпляр компонента <xref:System.Diagnostics.Process>, который можно использовать для остановки, запуска и изменения данных, связанных с процессами в системе.

 **SerialPort**

 Создает экземпляр компонента `System.IO.Ports.SerialPort`, который предоставляет средства для синхронного и управляемого событиями ввода-вывода, доступа к состоянию подключения-отключения устройства, а также для доступа к свойствам драйвера последовательного порта.

 **ServiceController**

 Создает экземпляр компонента <xref:System.ServiceProcess.ServiceController>, который можно использовать для управления существующими службами, включая запуск и остановку служб, а также передачу им команд.

 **Таймер**

 Создает экземпляр компонента <xref:System.Windows.Forms.Timer>, который можно использовать для добавления функций на основе времени для Windows-приложений. Дополнительную информацию см. в разделе [Компонент таймера](/dotnet/framework/winforms/controls/timer-component-windows-forms).

> [!NOTE]
> Существует также системный <xref:System.Timers.Timer>, который можно добавить на **панель элементов**. Этот компонент <xref:System.Timers.Timer> оптимизирован для серверных приложений и Windows Forms. <xref:System.Windows.Forms.Timer> лучше всего подходит для использования в формах Windows Forms.


## <a name="see-also"></a>См. также

- [Программирование с использованием компонентов](http://msdn.microsoft.com/Library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)
- [Пошаговые руководства программирования компонентов](http://msdn.microsoft.com/Library/373cacf7-479e-4b05-991c-5cb18824e913)
- [Панель элементов](../../ide/reference/toolbox.md)