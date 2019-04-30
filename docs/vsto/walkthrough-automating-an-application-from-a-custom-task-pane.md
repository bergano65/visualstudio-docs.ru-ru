---
title: Пошаговое руководство. Автоматизация приложения с настраиваемой области задач
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio], custom task panes
- automating Office applications
- custom task panes [Office development in Visual Studio], automating applications
- custom task panes [Office development in Visual Studio], PowerPoint
- task panes [Office development in Visual Studio], automating applications
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 38245a3c16c79806f495b76a0ae0d64b55c05623
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438725"
---
# <a name="walkthrough-automate-an-application-from-a-custom-task-pane"></a>Пошаговое руководство. Автоматизация приложения с настраиваемой области задач
  В этом пошаговом руководстве рассматриваются способы создания настраиваемой области задач, которая автоматизирует PowerPoint. Настраиваемая область задач вставляет даты в слайд, когда пользователь нажимает элемент управления <xref:System.Windows.Forms.MonthCalendar> в ней.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Хотя в этом пошаговом руководстве используется PowerPoint, рассмотренная процедура применима к любым перечисленным выше приложениям.

 В данном пошаговом руководстве рассмотрены следующие задачи:

- проектирование пользовательского интерфейса настраиваемой области задач;

- автоматизация PowerPoint в настраиваемой области задач;

- отображение настраиваемой области задач в PowerPoint.

> [!NOTE]
> Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Предварительные требования
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft PowerPoint 2010 или [!INCLUDE[PowerPoint_15_short](../vsto/includes/powerpoint-15-short-md.md)].

## <a name="create-the-add-in-project"></a>Создание проекта надстройки
 Первым шагом является создание проекта надстройки VSTO для PowerPoint.

### <a name="to-create-a-new-project"></a>Создание нового проекта

1. Создайте проект надстройки VSTO для PowerPoint с именем **MyAddIn**, используя шаблон проекта надстройки PowerPoint. Дополнительные сведения см. в разделе [Как Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] открывает файл кода **ThisAddIn.cs** или **ThisAddIn.vb** и добавляет проект **MyAddIn** в **обозреватель решений**.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Проектирование пользовательского интерфейса настраиваемой области задач
 Визуальный конструктор для настраиваемых областей задач не предусмотрен, но вы можете разработать собственный элемент управления с желаемой структурой. Далее в этом пошаговом руководстве вы добавите этот пользовательский элемент управления в настраиваемую область задач.

#### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Проектирование пользовательского интерфейса настраиваемой области задач

1. В меню **Проект** выберите команду **Добавить пользовательский элемент управления**.

2. В диалоговом окне **Добавление нового элемента** измените имя пользовательского элемента управления на **MyUserControl**и нажмите кнопку **Добавить**.

     Пользовательский элемент управления откроется в конструкторе.

3. Перетащите элемент управления **MonthCalendar** со вкладки **Стандартные элементы управления**на **панели элементов** в пользовательский элемент управления.

     Если элемент управления **MonthCalendar** больше поверхности конструктора пользовательского элемента управления, измените размер пользовательского элемента управления в соответствии с размерами элемента управления **MonthCalendar** .

## <a name="automate-powerpoint-from-the-custom-task-pane"></a>Автоматизация PowerPoint в настраиваемой области задач
 Задача надстройки VSTO состоит в том, чтобы разместить выбранную дату на первом слайде активной презентации. Используйте событие <xref:System.Windows.Forms.MonthCalendar.DateChanged> элемента управления, чтобы добавить выбранную дату при ее изменении.

### <a name="to-automate-powerpoint-from-the-custom-task-pane"></a>Автоматизация PowerPoint в настраиваемой области задач

1. В конструкторе дважды щелкните элемент управления <xref:System.Windows.Forms.MonthCalendar> .

     Откроется файл **MyUserControl.cs** или **MyUserControl.vb** , и будет создан обработчик событий <xref:System.Windows.Forms.MonthCalendar.DateChanged> .

2. Добавьте приведенный ниже код в начало файла. В этом коде создаются псевдонимы для пространств имен <xref:Microsoft.Office.Core> и <xref:Microsoft.Office.Interop.PowerPoint> .

     [!code-csharp[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#1)]
     [!code-vb[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#1)]

3. Добавьте следующий код в класс `MyUserControl` . Этот код объявляет объект <xref:Microsoft.Office.Interop.PowerPoint.Shape> как член класса `MyUserControl`. На следующем этапе мы будем использовать этот объект <xref:Microsoft.Office.Interop.PowerPoint.Shape> для добавления текстового поля на слайд активной презентации.

     [!code-csharp[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#2)]
     [!code-vb[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#2)]

4. Замените обработчик событий `monthCalendar1_DateChanged` следующим кодом. Этот код добавляет текстовое поле на первый слайд активной презентации, а затем вставляет в это поле выбранную дату. Код использует объект `Globals.ThisAddIn` для получения доступа к объектной модели PowerPoint.

     [!code-csharp[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#3)]
     [!code-vb[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#3)]

5. В **обозревателе решений**щелкните проект **MyAddIn** правой кнопкой мыши и выберите пункт **Сборка**. Убедитесь, что сборка проекта выполняется без ошибок.

## <a name="display-the-custom-task-pane"></a>Отображение настраиваемой области задач
 Для отображения настраиваемой области задач при запуске надстройки VSTO добавьте пользовательский элемент управления в область задач в обработчике событий <xref:Microsoft.Office.Tools.AddIn.Startup> надстройки VSTO.

### <a name="to-display-the-custom-task-pane"></a>Отображение настраиваемой области задач

1. В **обозревателе решений**разверните **PowerPoint**.

2. Щелкните правой кнопкой мыши файл **ThisAddIn.cs** или **ThisAddIn.vb** и выберите пункт **Просмотреть код**.

3. Добавьте следующий код в класс `ThisAddIn` . Этот код объявляет экземпляры `MyUserControl` и <xref:Microsoft.Office.Tools.CustomTaskPane> как члены класса `ThisAddIn` .

     [!code-vb[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#4)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#4)]

4. Замените обработчик событий `ThisAddIn_Startup` следующим кодом. Этот код создает новый объект <xref:Microsoft.Office.Tools.CustomTaskPane> , добавляя  объект `MyUserControl` в коллекцию `CustomTaskPanes` . Код также отображает область задач.

     [!code-vb[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#5)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#5)]

## <a name="test-the-add-in"></a>Тестирование надстройки
 При запуске проекта открывается приложение PowerPoint и надстройка отображает настраиваемую область задач. Чтобы протестировать код, щелкните элемент управления <xref:System.Windows.Forms.MonthCalendar> .

### <a name="to-test-your-vsto-add-in"></a>Для тестирования надстройки VSTO выполните следующие действия.

1. Нажмите клавишу **F5** для запуска проекта.

2. Убедитесь в том, что настраиваемая область задач видна.

3. Щелкните дату в элементе управления <xref:System.Windows.Forms.MonthCalendar> в области задач.

     Дата вставляется на первом слайде активной презентации.

## <a name="next-steps"></a>Следующие шаги
 Дополнительные сведения о создании настраиваемых областей задач см. в следующих разделах:

- Создание настраиваемой области задач в надстройке VSTO для другого приложения. Дополнительные сведения о приложениях, поддерживающих настраиваемые области задач, см. в разделе [настраиваемых панелей задач](../vsto/custom-task-panes.md).

- Создание кнопки ленты, которая может использоваться для скрытия или отображения настраиваемой области задач. Дополнительные сведения см. в разделе [Пошаговое руководство: Синхронизация настраиваемой области задач с кнопкой на ленте](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).

- Создание настраиваемой области задач для каждого сообщения электронной почты, открываемого в Outlook. Дополнительные сведения см. в разделе [Пошаговое руководство: Отображение настраиваемых областей задач с сообщениями электронной почты в Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).

## <a name="see-also"></a>См. также
- [Настраиваемые области задач](../vsto/custom-task-panes.md)
- [Практическое руководство. Добавление настраиваемой области задач в приложение](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Пошаговое руководство: Синхронизация настраиваемой области задач с кнопкой на ленте](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [Пошаговое руководство: Отображение настраиваемых областей задач с сообщениями электронной почты в Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
