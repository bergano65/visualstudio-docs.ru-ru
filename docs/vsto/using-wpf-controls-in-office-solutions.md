---
title: "Использование элементов управления WPF в решениях Office | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: WPF [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 74ee8c574f6f654aca166844d85a30f2d3d9d4c3
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="using-wpf-controls-in-office-solutions"></a>Использование элементов управления WPF в решениях Office
  Хотя решения, созданные с помощью средств разработки Office в Visual Studio, предназначены для работы непосредственно с элементами управления Windows Forms, в них также можно использовать элементы управления WPF. Windows Presentation Foundation (WPF) — это альтернатива Windows Forms для разработки пользовательских интерфейсов. WPF использует язык разметки XAML для реализации новых методов включения элементов пользовательского интерфейса, объектов мультимедиа и документов. Дополнительные сведения см. в разделе [введение в WPF в Visual Studio 2015](/dotnet/framework/wpf/getting-started/introduction-to-wpf-in-vs).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Любой элемент пользовательского интерфейса, который может содержать элементы управления Windows Forms в решении Office, может содержать и элементы управления WPF. К ним относятся:  
  
-   документы и книги в настройках уровня документа;  
  
-   панели действий в настройках уровня документа;  
  
-   настраиваемые области задач в надстройках VSTO;  
  
-   области формы в надстройках VSTO для Outlook.  
  
## <a name="adding-wpf-controls-to-office-projects-at-design-time"></a>Добавление элементов управления WPF в проекты Office во время разработки  
 Невозможно добавить элементы управления WPF напрямую в элементы пользовательского интерфейса в решениях Office. Вместо этого добавьте **пользовательский элемент управления (WPF)** в ваш проект и использовать в качестве рабочей области конструирования для элементов управления WPF. Затем добавьте пользовательский элемент управления WPF в элемент пользовательского интерфейса в проекте.  
  
#### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>Добавление элементов управления WPF в панель действий, настраиваемую область задач или область формы  
  
1.  Откройте проект, в который требуется добавить настраиваемую область задач, панель действий или область формы.  
  
2.  Добавить **пользовательский элемент управления (WPF)** в проект.  
  
3.  Из **элементов**, добавление элементов управления WPF в рабочую область конструирования пользовательского элемента управления WPF.  
  
     По умолчанию, когда конструктор пользовательских элементов управления WPF открыт **элементов** содержит только элементы управления WPF.  
  
4.  Выполните построение проекта.  
  
5.  Добавьте в проект панель действий, область формы или настраиваемую область задач:  
  
    -   Области формы добавьте **область формы Outlook** в проект. Дополнительные сведения см. в разделе [как: Добавление области формы в проект надстройки Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
    -   Панели действий добавьте **управления панели действий** или **пользовательский элемент управления** в проект. Дополнительные сведения см. в разделе [как: Добавление панели действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md) и [как: Добавление панели действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
    -   Настраиваемые области задач, добавьте **пользовательский элемент управления** в проект. Дополнительные сведения см. в разделе [как: добавление настраиваемой области задач в приложение](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
6.  Из *ProjectName* **пользовательские элементы управления WPF** вкладке **элементов**, перетащите пользовательский элемент управления WPF в конструктор панели действий, области формы или настраиваемой области задач.  
  
     Visual Studio автоматически создает объект <xref:System.Windows.Forms.Integration.ElementHost>, в котором размещается пользовательский элемент управления WPF, в элементе пользовательского интерфейса.  
  
7.  Перестройте проект.  
  
#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>Добавление элементов управления WPF в документ или на лист в проекте уровня документа  
  
1.  Откройте проект уровня документа для Word или Excel.  
  
2.  Добавить **пользовательский элемент управления (WPF)** в проект.  
  
3.  Из **элементов**, добавление элементов управления WPF в рабочую область конструирования пользовательского элемента управления WPF.  
  
4.  Выполните построение проекта.  
  
5.  Добавить **пользовательский элемент управления** в проект элемент (то есть пользовательский элемент управления Windows Forms).  
  
6.  Откройте конструктор пользовательского элемента управления Windows Forms.  
  
7.  Из *ProjectName* **пользовательские элементы управления WPF** вкладке **элементов**, перетащите пользовательский элемент управления WPF в конструктор.  
  
     Visual Studio автоматически создает объект <xref:System.Windows.Forms.Integration.ElementHost>, в котором размещается пользовательский элемент управления WPF, в пользовательском элементе управления Windows Forms.  
  
8.  Напишите код, который программными средствами добавляет пользовательский элемент управления Windows Forms в документ или на лист. Для получения дополнительной информации см. [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
    > [!NOTE]  
    >  В конструкторе невозможно перетащить пользовательский элемент управления Windows Forms в документ или на лист.  
  
9. Перестройте проект.  
  
## <a name="hosting-wpf-controls-by-using-the-elementhost-class"></a>Размещение элементов управления WPF с помощью класса ElementHost  
 Visual Studio предоставляет средства, помогающие использовать элементы управления Windows Forms в решениях Office, но не предоставляет аналогичные функциональные возможности для элементов управления WPF. Например, вы можно добавить элементы управления Windows Forms в документы и листы во время разработки, перетаскивая элементы из **элементов**, или во время выполнения с помощью вспомогательных методов. Однако эти средства недоступны для элементов управления WPF.  
  
 Элементы управления WPF используют класс <xref:System.Windows.Forms.Integration.ElementHost> как уровень интеграции между элементом управления или формой Windows Forms и элементом управления WPF. При добавлении элементов управления WPF в решение во время разработки Visual Studio автоматически создает объект <xref:System.Windows.Forms.Integration.ElementHost>.  
  
## <a name="wpf-resources"></a>Ресурсы WPF  
 Дополнительные сведения об архитектуре и проектировании для размещения элементов управления WPF в элементах управления и формах Windows Forms см. в следующих разделах:  
  
-   [Windows Forms и архитектура ввода взаимодействия WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)  
  
-   [Сопоставление свойств Windows Forms и WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)  
  
-   [Взаимодействие WPF и Windows Forms](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)  
  
-   [Элементы управления Windows Forms и эквивалентные элементы управления WPF](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)  
  
 Дополнительные сведения о добавлении элементов управления WPF к элементам управления и формам Windows Forms в Visual Studio во время разработки см. в следующих разделах:  
  
-   [Пошаговое руководство. Создание нового содержимого WPF для формы Windows Forms во время разработки](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)  
  
-   [Пошаговое руководство. Упорядочение содержимого WPF для формы Windows Forms во время разработки](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)  
  
-   [Пошаговое руководство. Применение стилей к содержимому WPF](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)  
  
## <a name="see-also"></a>См. также  
 [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)   
 [Элементы управления в документах Office Windows Forms](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Общие сведения о панели действий](../vsto/actions-pane-overview.md)   
 [Настраиваемые области задач](../vsto/custom-task-panes.md)   
 [Создание областей форм Outlook](../vsto/creating-outlook-form-regions.md)   
 [Как: Добавление панели действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Как: Добавление панели действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Как: добавление настраиваемой области задач в приложение](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Практическое руководство. Добавление области формы в проект надстройки Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)  
  
  