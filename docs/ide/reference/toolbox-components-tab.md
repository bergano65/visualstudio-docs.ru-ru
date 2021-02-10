---
title: Вкладка "Компоненты", панель элементов
description: Сведения о компонентах, которые можно найти на вкладке "Компоненты" панели элементов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.FrameworkComponents
- VS.CHOOSEITEMS.COMComponents
- VS.CHOOSEITEMS.UniversalWindowsComponents
helpviewer_keywords:
- Toolbox, Components tab
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: adbc2611cf0d0e08ef356e91e25ed0c4854c4386
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965048"
---
# <a name="toolbox-components-tab"></a>Панель элементов, вкладка "Компоненты"

Отображает компоненты, которые можно добавить в конструкторы Visual Basic и C# для Windows Forms. В дополнение к компонентам .NET, которые входят в состав Visual Studio (например, <xref:System.Messaging.MessageQueue> и <xref:System.Diagnostics.EventLog>), на этой вкладке можно добавить собственные или сторонние компоненты.

Чтобы отобразить эту вкладку, откройте конструктор Windows Forms. Выберите **Представление** > **Панель элементов**. На **панели элементов** выберите вкладку **Компоненты**.

## <a name="components"></a>Компоненты

**BackgroundWorker**

Создает экземпляр компонента <xref:System.ComponentModel.BackgroundWorker>, который может выполнять операцию в отдельном выделенном потоке. Дополнительную информацию см. в разделе [Компонент BackgroundWorker](/dotnet/framework/winforms/controls/backgroundworker-component).

**DirectoryEntry**

Создает экземпляр компонента <xref:System.DirectoryServices.DirectoryEntry>, который инкапсулирует узел или объект в иерархии Active Directory и может использоваться для взаимодействия с поставщиками служб Active Directory.

**DirectorySearcher**

Создает экземпляр компонента <xref:System.DirectoryServices.DirectorySearcher>, который можно использовать для выполнения запросов к Active Directory.

**ErrorProvider**

Создает экземпляр компонента <xref:System.Windows.Forms.ErrorProvider>, который указывает конечному пользователю, что с элементом управления в форме связана ошибка. Дополнительную информацию см. в разделе [Компонент ErrorProvider](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

**EventLog**

Создает экземпляр компонента <xref:System.Diagnostics.EventLog>, который можно использовать для взаимодействия с системой и пользовательскими журналами событий, включая запись событий в журнал и чтения данных журнала.

**FileSystemWatcher**

Создает экземпляр компонента <xref:System.IO.FileSystemWatcher>, который можно использовать для отслеживания изменений в любом каталоге или файле, к которому имеется доступ.

**HelpProvider**

Создает экземпляр компонента <xref:System.Windows.Forms.HelpProvider>, который обеспечивает для элементов управления всплывающее окно справки или окно оперативной справки. Дополнительную информацию см. в разделе [Компонент HelpProvider](/dotnet/framework/winforms/controls/helpprovider-component-windows-forms).

**ImageList**

Создает экземпляр компонента <xref:System.Windows.Forms.ImageList>, который предоставляет методы для управления коллекцией объектов <xref:System.Drawing.Image>. Дополнительную информацию см. в разделе [Компонент ImageList](/dotnet/framework/winforms/controls/imagelist-component-windows-forms).

**MessageQueue**

Создает экземпляр компонента <xref:System.Messaging.MessageQueue>, который можно использовать для взаимодействия с очередями сообщений, включая чтение сообщений из очередей и запись их туда, обработка транзакций и выполнение задач администрирования очередей.

**PerformanceCounter**

Создает экземпляр компонента <xref:System.Diagnostics.PerformanceCounter>, который можно использовать для взаимодействия со счетчиками производительности Windows, включая создание новых категорий и экземпляров, чтения значений из счетчиков и выполнения вычислений на основе данных счетчиков.

**Process**

Создает экземпляр компонента <xref:System.Diagnostics.Process>, который можно использовать для остановки, запуска и изменения данных, связанных с процессами в системе.

**SerialPort**

Создает экземпляр компонента <xref:System.IO.Ports.SerialPort>, который предоставляет средства для синхронного и управляемого событиями ввода-вывода, доступа к состоянию подключения-отключения устройства, а также для доступа к свойствам драйвера последовательного порта.

**ServiceController**

Создает экземпляр компонента <xref:System.ServiceProcess.ServiceController>, который можно использовать для управления существующими службами, включая запуск и остановку служб, а также передачу им команд.

**Таймер**

Создает экземпляр компонента <xref:System.Windows.Forms.Timer>, который можно использовать для добавления функций на основе времени для Windows-приложений. Дополнительную информацию см. в разделе [Компонент Timer](/dotnet/framework/winforms/controls/timer-component-windows-forms).

> [!NOTE]
> Существует также системный <xref:System.Timers.Timer>, который можно добавить на **панель элементов**. Этот компонент <xref:System.Timers.Timer> оптимизирован для серверных приложений и Windows Forms. <xref:System.Windows.Forms.Timer> лучше всего подходит для использования в формах Windows Forms.

## <a name="see-also"></a>См. также раздел

- [Элементы управления для использования в Windows Forms](/dotnet/framework/winforms/controls/controls-to-use-on-windows-forms)
- [Выбор элементов панели элементов — компоненты WPF](choose-toolbox-items-wpf-components.md)
- [Панель элементов](../../ide/reference/toolbox.md)
