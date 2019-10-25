---
title: Панель элементов, вкладка "Компоненты" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Toolbox, Components tab
ms.assetid: 332fafab-a763-4244-b388-15d1b5b5cc04
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ce18767d95b3ac539737d78acbd2259dcda0a036
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661568"
---
# <a name="toolbox-components-tab"></a>Вкладка "Компоненты", панель элементов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Отображает компоненты, которые можно добавить в конструкторы [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] и [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. В дополнение к компонентам [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], которые входят в состав [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], таким как <xref:System.Messaging.MessageQueue> и <xref:System.Diagnostics.EventLog>, на этой вкладке можно добавить собственные или сторонние компоненты. Для получения дополнительной информации см. раздел [Практическое руководство. Управление вкладками панели элементов](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).

 Чтобы отобразить эту вкладку, в меню **Вид** выберите пункт **Панель элементов**. В **панели элементов** выберите вкладку **Компоненты**.

 **BackgroundWorker** Создает `System.ComponentModel.BackgroundWorker` экземпляр компонента, который может выполнять операцию в отдельном выделенном потоке.

 **DirectoryEntry** Создает <xref:System.DirectoryServices.DirectoryEntry> экземпляр компонента, который инкапсулирует узел или объект в иерархии Active Directory и может использоваться для взаимодействия с поставщиками служб Active Directory.

 **DirectorySearcher** Создает экземпляр компонента <xref:System.DirectoryServices.DirectorySearcher>, который можно использовать для выполнения запросов к Active Directory.

 **ErrorProvider** Создает экземпляр компонента `System.Windows.Forms.ErrorProvider`, который указывает конечному пользователю, что с элементом управления в форме связана ошибка.

 **Журнал событий** Создает экземпляр компонента <xref:System.Diagnostics.EventLog>, который можно использовать для взаимодействия с системными и пользовательскими журналами событий, включая запись событий в журнал и чтение данных журнала. Дополнительные сведения см. в разделе [Знакомство с компонентом EventLog](https://msdn.microsoft.com/a2ba4f28-4b1a-435e-99ef-51b28e21f805).

 **FileSystemWatcher** Создает экземпляр компонента <xref:System.IO.FileSystemWatcher>, который можно использовать для отслеживания изменений в любом каталоге или файле, к которому у вас есть доступ. Дополнительные сведения см. в разделе [Практическое руководство. Настройка экземпляров компонента FileSystemWatcher](https://msdn.microsoft.com/2e628234-4951-4135-8a86-28b924070d50).

 **HelpProvider** Создает экземпляр компонента `System.Windows.Forms.HelpProvider`, предоставляющий всплывающее окно справки для элементов управления или справку в Интернете.

 **ImageList** Создает экземпляр компонента `System.Windows.Forms.ImageList`, предоставляющий методы для управления коллекцией `System.Drawing.Image` объектов.

 **MessageQueue** Создает экземпляр компонента <xref:System.Messaging.MessageQueue>, который можно использовать для взаимодействия с очередями сообщений, включая чтение сообщений из очередей и запись сообщений в очереди, обработку транзакций и выполнение задач администрирования очередей. Дополнительные сведения см. в разделе [Использование компонентов для обмена сообщениями](https://msdn.microsoft.com/922dbac7-26f0-4e39-b666-ccfc184793d7).

 **PerformanceCounter** Создает экземпляр компонента <xref:System.Diagnostics.PerformanceCounter>, который можно использовать для взаимодействия со счетчиками производительности Windows, включая создание новых категорий и экземпляров, чтение значений из счетчиков и выполнение вычислений с данными счетчиков. Дополнительные сведения см. в разделе [Отслеживание пороговых значений производительности](https://msdn.microsoft.com/b8b44a55-31d0-4b45-9517-8c1b1e4fdc91).

 **Обработка** Создает экземпляр компонента <xref:System.Diagnostics.Process>, который можно использовать для завершения, запуска и обработки данных, связанных с процессами в системе. Дополнительные сведения см. в разделе [Мониторинг процессов Windows и управление ими](https://msdn.microsoft.com/a86bd4c1-b92c-49a0-8f32-61d67837b45e).

 **SerialPort** Создает экземпляр компонента `System.IO.Ports.SerialPort`, который обеспечивает синхронный и управляемый событиями ввод-вывод, доступ к состояниям ПИН-кода и прерываний, а также доступ к свойствам последовательного драйвера.

 **ServiceController** Создает экземпляр компонента <xref:System.ServiceProcess.ServiceController>, который можно использовать для управления существующими службами, включая запуск и остановку служб, а также отправку команд. Дополнительные сведения см. в разделе[Мониторинг служб Windows](https://msdn.microsoft.com/4542ee3f-e052-4cb9-8726-58e9420de222).

 **Таймер** Создает <xref:System.Windows.Forms.Timer> экземпляр компонента, который можно использовать для добавления функциональности на основе времени в приложения Windows. Дополнительную информацию см. в разделе [Компонент таймера](https://msdn.microsoft.com/library/6700e534-6382-43d5-98ed-14205435fff7).

> [!NOTE]
> Существует также системный <xref:System.Timers.Timer>, который можно добавить на **панель элементов**. Этот компонент <xref:System.Timers.Timer> оптимизирован для серверных приложений и Windows Forms. <xref:System.Windows.Forms.Timer> лучше всего подходит для использования в формах Windows Forms.

## <a name="see-also"></a>См. также
 [Программирование с помощью компонентов ](https://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3) [Component пошаговые руководства по программированию ](https://msdn.microsoft.com/library/373cacf7-479e-4b05-991c-5cb18824e913) [Toolbox ](../../ide/reference/toolbox.md) [диалоговое окно "элементы панели элементов" (Visual Studio)](https://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb)
