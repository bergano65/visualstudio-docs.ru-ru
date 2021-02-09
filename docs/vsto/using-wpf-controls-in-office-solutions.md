---
title: Использование элементов управления WPF в решениях Office
description: Узнайте, как можно использовать элементы управления Windows Presentation Foundation (WPF) для разработки пользовательских интерфейсов в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7bc720e6218e4cbb76b14f356d190b738e31ede3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921900"
---
# <a name="use-wpf-controls-in-office-solutions"></a>Использование элементов управления WPF в решениях Office

Хотя решения, созданные с помощью средств разработки Office в Visual Studio, предназначены для работы непосредственно с элементами управления Windows Forms, в них также можно использовать элементы управления WPF. Windows Presentation Foundation (WPF) — это альтернатива Windows Forms для разработки пользовательских интерфейсов. WPF использует язык разметки XAML для реализации новых методов включения элементов пользовательского интерфейса, объектов мультимедиа и документов. Дополнительные сведения см. в разделе [Общие сведения о WPF](/dotnet/framework/wpf/introduction-to-wpf).

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

Любой элемент пользовательского интерфейса, который может содержать элементы управления Windows Forms в решении Office, может содержать и элементы управления WPF. К ним относятся:

- документы и книги в настройках уровня документа;

- панели действий в настройках уровня документа;

- настраиваемые области задач в надстройках VSTO;

- области формы в надстройках VSTO для Outlook.

## <a name="add-wpf-controls-to-office-projects-at-design-time"></a>Добавление элементов управления WPF в проекты Office во время разработки

Невозможно добавить элементы управления WPF напрямую в элементы пользовательского интерфейса в решениях Office. Вместо этого добавьте элемент **пользовательского элемента управления (WPF)** в проект и используйте его в качестве области конструктора для элементов управления WPF. Затем добавьте пользовательский элемент управления WPF в элемент пользовательского интерфейса в проекте.

### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>Добавление элементов управления WPF в панель действий, настраиваемую область задач или область формы

1. Откройте проект, в который требуется добавить настраиваемую область задач, панель действий или область формы.

2. Добавьте элемент **пользовательского элемента управления (WPF)** в проект.

3. Из **панели элементов** добавьте элементы управления WPF в рабочую область конструирования пользовательского элемента управления WPF.

     По умолчанию, когда конструктор пользовательского элемента управления WPF открыт, **панель элементов** содержит только элементы управления WPF.

4. Выполните построение проекта.

5. Добавьте в проект панель действий, область формы или настраиваемую область задач:

    - Для областей формы добавьте в проект элемент **области формы Outlook** . Дополнительные сведения см. в разделе [инструкции. Добавление области формы в проект надстройки Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

    - Для панелей действий добавьте **элемент управления панели действий** или элемент **пользовательского элемента управления** в проект. Дополнительные сведения см. в разделе [руководство. Добавление панели действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

    - Для настраиваемых областей задач добавьте в проект элемент **пользовательского элемента управления** . Дополнительные сведения см. в разделе [инструкции. Добавление настраиваемой области задач в приложение](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

6. Перетащите пользовательский элемент управления WPF с вкладки **элементы пользовательского** элемента управления " *имя_проекта* WPF" **панели элементов** в конструктор для панели действий, области формы или настраиваемой области задач.

     Visual Studio автоматически создает объект <xref:System.Windows.Forms.Integration.ElementHost>, в котором размещается пользовательский элемент управления WPF, в элементе пользовательского интерфейса.

7. Выполните повторную сборку проекта.

#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>Добавление элементов управления WPF в документ или на лист в проекте уровня документа

1. Откройте проект уровня документа для Word или Excel.

2. Добавьте элемент **пользовательского элемента управления (WPF)** в проект.

3. Из **панели элементов** добавьте элементы управления WPF в рабочую область конструирования пользовательского элемента управления WPF.

4. Выполните построение проекта.

5. Добавьте элемент **пользовательского элемента управления** (то есть Windows Forms пользовательский элемент управления) в проект.

6. Откройте конструктор пользовательского элемента управления Windows Forms.

7. Перетащите пользовательский элемент управления WPF с вкладки " **пользовательские элементы управления WPF** *" на* **панели элементов** в конструктор.

     Visual Studio автоматически создает объект <xref:System.Windows.Forms.Integration.ElementHost>, в котором размещается пользовательский элемент управления WPF, в пользовательском элементе управления Windows Forms.

8. Напишите код, который программными средствами добавляет пользовательский элемент управления Windows Forms в документ или на лист. Дополнительные сведения см. [в разделе Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).

    > [!NOTE]
    > В конструкторе невозможно перетащить пользовательский элемент управления Windows Forms в документ или на лист.

9. Выполните повторную сборку проекта.

## <a name="host-wpf-controls-by-using-the-elementhost-class"></a>Размещение элементов управления WPF с помощью класса ElementHost

Visual Studio предоставляет средства, помогающие использовать элементы управления Windows Forms в решениях Office, но не предоставляет аналогичные функциональные возможности для элементов управления WPF. Например, можно добавлять элементы управления Windows Forms в документы и листы во время разработки, перетаскивая элементы управления из **панели элементов** или во время выполнения с помощью вспомогательных методов. Однако эти средства недоступны для элементов управления WPF.

Элементы управления WPF используют класс <xref:System.Windows.Forms.Integration.ElementHost> как уровень интеграции между элементом управления или формой Windows Forms и элементом управления WPF. При добавлении элементов управления WPF в решение во время разработки Visual Studio автоматически создает объект <xref:System.Windows.Forms.Integration.ElementHost>.

## <a name="wpf-resources"></a>Ресурсы WPF

Дополнительные сведения об архитектуре и проектировании для размещения элементов управления WPF в элементах управления и формах Windows Forms см. в следующих разделах:

- [Windows Forms и архитектура ввода взаимодействия WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)

- [Сопоставление свойств Windows Forms и WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)

- [Взаимодействие WPF и Windows Forms](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)

- [Элементы управления Windows Forms и эквивалентные элементы управления WPF](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)

Дополнительные сведения о добавлении элементов управления WPF к элементам управления и формам Windows Forms в Visual Studio во время разработки см. в следующих разделах:

- [Пошаговое руководство. Создание нового содержимого WPF на Windows Forms во время разработки](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)

- [Пошаговое руководство. размещение содержимого WPF на Windows Forms во время разработки](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)

- [Пошаговое руководство. стиль содержимого WPF](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)

## <a name="see-also"></a>См. также раздел

- [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)
- [Общие сведения об элементах управления Windows Forms в документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Обзор панели действий](../vsto/actions-pane-overview.md)
- [Настраиваемые области задач](../vsto/custom-task-panes.md)
- [Создание областей формы Outlook](../vsto/creating-outlook-form-regions.md)
- [Как добавить панель действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Как добавить настраиваемую область задач в приложение](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Как добавить область формы в проект надстройки Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
