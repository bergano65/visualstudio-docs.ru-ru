---
title: Использование элементов управления WPF в решениях Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5419a715cbe255b5cfc31a113a00e3525d63d827
ms.sourcegitcommit: 96a6d1f16d06ca28d309d05b6e9fbd52f628cdbc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2018
ms.locfileid: "40008207"
---
# <a name="use-wpf-controls-in-office-solutions"></a>Использование элементов управления WPF в решениях Office

Хотя решения, созданные с помощью средств разработки Office в Visual Studio, предназначены для работы непосредственно с элементами управления Windows Forms, в них также можно использовать элементы управления WPF. Windows Presentation Foundation (WPF) — это альтернатива Windows Forms для разработки пользовательских интерфейсов. WPF использует язык разметки XAML для реализации новых методов включения элементов пользовательского интерфейса, объектов мультимедиа и документов. Дополнительные сведения см. в разделе [Общие сведения о WPF](../designers/introduction-to-wpf.md).

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

Любой элемент пользовательского интерфейса, который может содержать элементы управления Windows Forms в решении Office, может содержать и элементы управления WPF. К ним относятся:

-   документы и книги в настройках уровня документа;

-   панели действий в настройках уровня документа;

-   настраиваемые области задач в надстройках VSTO;

-   области формы в надстройках VSTO для Outlook.

## <a name="add-wpf-controls-to-office-projects-at-design-time"></a>Добавление элементов управления WPF в проекты Office во время разработки

Невозможно добавить элементы управления WPF напрямую в элементы пользовательского интерфейса в решениях Office. Вместо этого добавьте **пользовательский элемент управления (WPF)** элемента в проект и использовать его в качестве рабочей области конструирования для элементов управления WPF. Затем добавьте пользовательский элемент управления WPF в элемент пользовательского интерфейса в проекте.

### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>Добавление элементов управления WPF в панель действий, настраиваемую область задач или область формы

1.  Откройте проект, в который требуется добавить настраиваемую область задач, панель действий или область формы.

2.  Добавить **пользовательский элемент управления (WPF)** в проект.

3.  Из **элементов**, добавление элементов управления WPF в рабочую область конструирования пользовательского элемента управления WPF.

     По умолчанию, когда конструктор пользовательских элементов управления WPF открыт **элементов** содержит только элементы управления WPF.

4.  Выполните построение проекта.

5.  Добавьте в проект панель действий, область формы или настраиваемую область задач:

    -   Для областей формы добавьте **область формы Outlook** элемента в проект. Дополнительные сведения см. в разделе [как: Добавление области формы в проект надстройки Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

    -   Для панелей действий, добавьте **элемента управления панели действий** или **пользовательский элемент управления** в проект элемент. Дополнительные сведения см. в разделе [как: Добавление панели действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md) и [как: Добавление панели действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

    -   Настраиваемые области задач, добавьте **пользовательский элемент управления** в проект элемент. Дополнительные сведения см. в разделе [как: добавление настраиваемой области задач в приложение](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

6.  Из *имя_проекта* **пользовательские элементы управления WPF** вкладке **элементов**, перетащите пользовательский элемент управления WPF в конструктор для панели действий, область формы или настраиваемой области задач.

     Visual Studio автоматически создает объект <xref:System.Windows.Forms.Integration.ElementHost>, в котором размещается пользовательский элемент управления WPF, в элементе пользовательского интерфейса.

7.  Перестройте проект.

#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>Добавление элементов управления WPF в документ или на лист в проекте уровня документа

1.  Откройте проект уровня документа для Word или Excel.

2.  Добавить **пользовательский элемент управления (WPF)** в проект.

3.  Из **элементов**, добавление элементов управления WPF в рабочую область конструирования пользовательского элемента управления WPF.

4.  Выполните построение проекта.

5.  Добавить **пользовательский элемент управления** в проект элемент (то есть пользовательский элемент управления Windows Forms).

6.  Откройте конструктор пользовательского элемента управления Windows Forms.

7.  Из *имя_проекта* **пользовательские элементы управления WPF** вкладке **элементов**, перетащите пользовательский элемент управления WPF в конструктор.

     Visual Studio автоматически создает объект <xref:System.Windows.Forms.Integration.ElementHost>, в котором размещается пользовательский элемент управления WPF, в пользовательском элементе управления Windows Forms.

8.  Напишите код, который программными средствами добавляет пользовательский элемент управления Windows Forms в документ или на лист. Дополнительные сведения см. в разделе [добавить элементы управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).

    > [!NOTE]
    > В конструкторе невозможно перетащить пользовательский элемент управления Windows Forms в документ или на лист.

9. Перестройте проект.

## <a name="host-wpf-controls-by-using-the-elementhost-class"></a>Элементы управления ведущего приложения WPF с помощью класса ElementHost

Visual Studio предоставляет средства, помогающие использовать элементы управления Windows Forms в решениях Office, но не предоставляет аналогичные функциональные возможности для элементов управления WPF. Например, вы можно добавить элементы управления Windows Forms в документы и листы во время разработки, перетаскивая элементы из **элементов**, или во время выполнения с помощью вспомогательных методов. Однако эти средства недоступны для элементов управления WPF.

Элементы управления WPF используют класс <xref:System.Windows.Forms.Integration.ElementHost> как уровень интеграции между элементом управления или формой Windows Forms и элементом управления WPF. При добавлении элементов управления WPF в решение во время разработки Visual Studio автоматически создает объект <xref:System.Windows.Forms.Integration.ElementHost>.

## <a name="wpf-resources"></a>Ресурсы WPF

Дополнительные сведения об архитектуре и проектировании для размещения элементов управления WPF в элементах управления и формах Windows Forms см. в следующих разделах:

-   [Архитектура ввода взаимодействия Windows Forms и WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)

-   [Сопоставление свойств Windows Forms и WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)

-   [Взаимодействие WPF и Windows Forms](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)

-   [Элементы управления Windows Forms и эквивалентные элементы управления WPF](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)

Дополнительные сведения о добавлении элементов управления WPF к элементам управления и формам Windows Forms в Visual Studio во время разработки см. в следующих разделах:

-   [Пошаговое руководство: Создание нового содержимого WPF в формах Windows Forms во время разработки](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)

-   [Пошаговое руководство: Размещение содержимого WPF в формах Windows Forms во время разработки](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)

-   [Пошаговое руководство: Стиль содержимого WPF](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)

## <a name="see-also"></a>См. также

- [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)
- [Элементы управления Windows Forms на общие сведения о документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Общие сведения о панели действий](../vsto/actions-pane-overview.md)
- [Настраиваемые области задач](../vsto/custom-task-panes.md)
- [Создание областей форм Outlook](../vsto/creating-outlook-form-regions.md)
- [Практическое: Добавление панели действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Практическое: добавление настраиваемой области задач в приложение](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Практическое: Добавление области формы в проект надстройки Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
