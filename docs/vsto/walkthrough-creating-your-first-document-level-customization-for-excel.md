---
title: Пошаговое руководство. Создание первой настройки уровня документа для Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Excel [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eaf5fe98e5c5a9c54245307f50e71345d0e2d477
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871251"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-excel"></a>Пошаговое руководство. Создание первой настройки уровня документа для Excel
  В этом вводном пошаговом руководстве показано, как создавать настройку на уровне документа для Microsoft Office Excel. Функциональные возможности, создаваемые в таком решения, доступны только в том случае, когда открыта конкретная книга. Для внесения изменений в приложение настройки на уровне документа использовать нельзя (например, для отображения новой вкладки ленты, когда открыта любая книга).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
- создание проекта книги Excel;  
  
- добавление текста в книгу, которая размещена в конструкторе Visual Studio;  
  
- написание кода, использующего объектную модель Excel для добавления текста в настраиваемую книгу при ее открытии;  
  
- Построение и запуск проекта для тестирования.  
  
- очистка готового проекта для удаления ненужных файлов сборки и параметров безопасности на компьютере разработчика.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] или [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="create-the-project"></a>Создание проекта  
  
### <a name="to-create-a-new-excel-workbook-project-in-visual-studio"></a>Создание проекта книги Excel в Visual Studio  
  
1. Запустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2. В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.  
  
3. В области шаблонов разверните узел **Visual C#** или **Visual Basic**, а затем узел **Office/SharePoint**.  
  
4. В развернутом узле **Office/SharePoint** выберите узел **Надстройки Office** .  
  
5. В списке шаблонов проектов выберите шаблон проекта надстройки VSTO для Excel.  
  
6. В **имя** введите **FirstWorkbookCustomization**.  
  
7. Нажмите кнопку **ОК**.  
  
    Откроется **Мастер проектов набора средств Visual Studio для Office** .  
  
8. Выберите **создания документа**и нажмите кнопку **ОК**.  
  
   - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Создает **FirstWorkbookCustomization** проекта, а также добавляет в проект следующие файлы.  
  
   - *FirstWorkbookCustomization*.xlsx представляет книгу Excel в проекте. Содержит все листы и диаграммы.  
  
   - Sheet1 (*.vb* файл для Visual Basic или *.cs* файл для Visual C#) — лист, предоставляющий рабочую область конструирования и код для первого листа в книге. Дополнительные сведения см. в разделе [ведущий элемент листа](../vsto/worksheet-host-item.md).  
  
   - Sheet2 (*.vb* файл для Visual Basic или *.cs* файл для Visual C#) — лист, предоставляющий рабочую область конструирования и код для второго листа в книге.  
  
   - Sheet3 (*.vb* файл для Visual Basic или *.cs* файл для Visual C#) — лист, предоставляющий рабочую область конструирования и код для третьего листа в книге.  
  
   - ThisWorkbook (*.vb* файл для Visual Basic или *.cs* файл для Visual C#) — содержит рабочую область конструирования и код для настроек на уровне книги. Дополнительные сведения см. в разделе [ведущий элемент книги](../vsto/workbook-host-item.md).  
  
     Файл кода Sheet1 автоматически открывается в конструкторе.  
  
## <a name="close-and-reopen-worksheets-in-the-designer"></a>Закройте и снова откройте листов в конструкторе  
 Если вы случайно или преднамеренно закрыли книгу или лист в конструкторе во время разработки проекта, их можно снова открыть.  
  
### <a name="to-close-and-reopen-a-worksheet-in-the-designer"></a>Закрытие и повторное открытие листа в конструкторе  
  
1.  Закрыть книгу, щелкнув **закрыть** кнопку (X) в окне конструктора.  
  
2.  В **обозревателе решений**, щелкните правой кнопкой мыши **Sheet1** файл кода, а затем нажмите кнопку **конструктор представлений**.  
  
     \- или -  
  
     В **обозревателе решений**, дважды щелкните **Sheet1** файл кода.  
  
## <a name="add-text-to-a-worksheet-in-the-designer"></a>Добавление текста на лист в конструкторе  
 Для разработки пользовательского интерфейса (UI) настройки можно изменить лист, который открыт в конструкторе. Например, можно добавить текст в ячейки, применить формулы или добавить элементы управления Excel. Дополнительные сведения об использовании конструктора см. в разделе [проекты Office в среде Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
### <a name="to-add-text-to-a-worksheet-by-using-the-designer"></a>Добавление текста на лист с помощью конструктора  
  
1.  На листе, который открыт в конструкторе, выделите ячейку **A1**, а затем введите следующий текст.  
  
     **Этот текст добавляется с помощью конструктора.**  
  
> [!WARNING]  
>  Если добавить эту строку текста в ячейку **A2**, она будет перезаписана другим кодом в этом примере.  
  
## <a name="add-text-to-a-worksheet-programmatically"></a>Добавление текста на лист программными средствами  
 Затем добавьте код в файл кода Sheet1. Новый код использует объектную модель Excel для добавления второй строки текста в книгу. По умолчанию файл кода Sheet1 содержит следующий созданный код:  
  
-   Частичное определение класса `Sheet1`, который представляет модель программирования листа и предоставляет доступ к объектной модели Excel. Дополнительные сведения [ведущий элемент листа](../vsto/worksheet-host-item.md) и [обзор объектной модели Word](../vsto/word-object-model-overview.md). Остальная часть класса `Sheet1` определяется в скрытом файле кода, изменять который не следует.  
  
-   Обработчики событий `Sheet1_Startup` и `Sheet1_Shutdown` . Эти обработчики событий вызываются, когда Excel загружает и выгружает настройку. Их можно использовать для инициализации настройки в процессе ее загрузки, а также для освобождения используемых настройкой ресурсов при ее выгрузке. Дополнительные сведения см. в разделе [события в проектах Office](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-a-second-line-of-text-to-the-worksheet-by-using-code"></a>Добавление второй строки текста на лист с помощью кода  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **Sheet1**, а затем нажмите кнопку **Просмотр кода**.  
  
     Файл кода открывается в Visual Studio.  
  
2.  Замените обработчик событий `Sheet1_Startup` следующим кодом. Когда Sheet1 открывается, этот код добавляет вторую строку текста на лист.  
  
     [!code-csharp[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelWorkbookTutorial/Sheet1.cs#1)]
     [!code-vb[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelWorkbookTutorial/Sheet1.vb#1)]  
  
## <a name="test-the-project"></a>Тестирование проекта  
  
### <a name="to-test-your-workbook"></a>Проверка книги  
  
1.  Нажмите клавишу **F5** для построения и запуска проекта.  
  
     При построении проекта код компилируется в сборку, которая связана с книгой. Visual Studio помещает копию книги и сборку в выходную папку построения для проекта и настраивает параметры безопасности на компьютере разработчика, чтобы разрешить выполнение настройки. Дополнительные сведения см. в разделе [решений Office построения](../vsto/building-office-solutions.md).  
  
2.  Убедитесь, что в книге отображается следующий текст.  
  
     **Этот текст добавляется с помощью конструктора.**  
  
     **Этот текст добавляется с помощью кода.**  
  
3.  Закройте книгу.  
  
## <a name="clean-up-the-project"></a>Очистка проекта  
 После завершения разработки проекта следует удалить файлы в выходной папке сборки и параметры безопасности, созданные в процессе сборки.  
  
### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Очистка завершенного проекта на компьютере разработчика  
  
1.  В Visual Studio в меню **Построение** выберите пункт **Очистить решение**.  
  
## <a name="next-steps"></a>Следующие шаги  
 Теперь после создания базовой настройки на уровне документа для Excel в следующих разделах можно ознакомиться с процессом разработки настроек:  
  
-   Общие задачи программирования, которые можно выполнять в настройках уровня документа: [Программирование настроек уровня документа](../vsto/programming-document-level-customizations.md).  
  
-   Задачи программирования, характерные для настроек уровня документа для Excel: [Решения Excel](../vsto/excel-solutions.md).  
  
-   С помощью объектной модели Excel: [Обзор объектной модели Excel](../vsto/excel-object-model-overview.md).  
  
-   Настройка пользовательского интерфейса Excel, например, путем добавления настраиваемой вкладки на ленту или создания собственной панели действий. [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).  
  
-   Использование расширенных объектов Excel, предоставляются средствами разработки Office в Visual Studio для выполнения задач, которые невозможно выполнить с помощью объектной модели Excel (например, размещение управляемых элементов управления в документах и привязка элементов управления Excel к данным с помощью Windows Forms модель привязки данных): [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md).  
  
-   Построение и отладка настроек на уровне документа для Excel: [Создание решений Office](../vsto/building-office-solutions.md).  
  
-   Развертывание настроек уровня документа для Excel: [Развертывание решения Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Решения Excel](../vsto/excel-solutions.md)   
 [Программирование настроек уровня документа](../vsto/programming-document-level-customizations.md)   
 [Обзор объектной модели Excel](../vsto/excel-object-model-overview.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)   
 [Создание решений Office](../vsto/building-office-solutions.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)   
 [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md)  
