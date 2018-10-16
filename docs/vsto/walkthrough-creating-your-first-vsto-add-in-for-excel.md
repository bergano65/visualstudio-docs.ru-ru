---
title: 'Пошаговое руководство: Создание первой надстройки VSTO для Excel'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Excel [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6421df0109d68d2647cafff5713aecb297c3536d
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38797803"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-excel"></a>Пошаговое руководство: Создание первой надстройки VSTO для Excel
  В этом вводном пошаговом руководстве показано, как создавать надстройки уровня приложения для Microsoft Office Excel. Функции, создаваемые в подобном решении, доступны для приложения независимо от того, какие книги открыты.  
  
 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   Создание проекта надстройки VSTO Excel для Excel.  
  
-   Написание кода с использованием объектной модели Excel, которая при сохранении книги добавляет в нее текст.  
  
-   Построение и запуск проекта для тестирования.  
  
-   Удаление завершенного проекта для прекращения автоматического запуска надстройки VSTO на компьютере разработчика.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] или [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="create-the-project"></a>Создание проекта  
  
#### <a name="to-create-a-new-excel-vsto-add-in-project-in-visual-studio"></a>Создание проекта надстройки VSTO Excel в Visual Studio  
  
1.  Запустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.  
  
3.  В области шаблонов разверните узел **Visual C#** или **Visual Basic**, а затем узел **Office/SharePoint**.  
  
4.  В развернутом узле **Office/SharePoint** выберите узел **Надстройки Office** .  
  
5.  В списке шаблонов проектов выберите **Надстройку Excel 2010** или **Надстройку Excel 2013**.  
  
6.  В поле **Имя** введите **FirstExcelAddIn**.  
  
7.  Нажмите кнопку **ОК**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] создает проект **FirstExcelAddIn** и открывает файл кода ThisAddIn в редакторе.  
  
## <a name="write-code-to-add-text-to-the-saved-workbook"></a>Написать код для добавления текста в сохраненную книгу  
 Затем добавьте код в файл ThisAddIn. Новый код использует объектную модель Excel для вставки стандартного текста в первую строку активного листа. Активным является лист, открытый в момент сохранения книги пользователем. По умолчанию файл кода ThisAddIn содержит следующий созданный код:  
  
-   Частичное определение класса `ThisAddIn` . Этот класс предоставляет точку входа для кода и обеспечивает доступ к объектной модели Excel. Дополнительные сведения см. в разделе [программы VSTO Add-ins](../vsto/programming-vsto-add-ins.md). Остальная часть класса `ThisAddIn` определяется в скрытом файле кода, изменять который не следует.  
  
-   Обработчики событий `ThisAddIn_Startup` и `ThisAddIn_Shutdown` . Эти обработчики событий вызываются, когда Excel загружает и выгружает надстройку VSTO. Их можно использовать для инициализации надстройки VSTO в процессе ее загрузки, а также для освобождения используемых надбавкой ресурсов при ее выгрузке. Дополнительные сведения см. в разделе [события в проектах Office](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-a-line-of-text-to-the-saved-workbook"></a>Добавление строки текста в сохраненную книгу  
  
1.  В файл кода ThisAddIn добавьте в класс `ThisAddIn` указанный ниже код. Новый код определяет обработчик событий для события <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> , которое возникает при сохранении книги.  
  
     Когда пользователь сохраняет книгу, обработчик событий добавляет новый текст в начало активного листа.  
  
     [!code-vb[Trin_ExcelAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInTutorial/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ExcelAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs#1)]  
  
2.  Если используется C#, добавьте в обработчик событий `ThisAddIn_Startup` указанный ниже код. Он используется для подключения обработчика событий `Application_WorkbookBeforeSave` к событию <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> .  
  
     [!code-csharp[Trin_ExcelAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInTutorial/ThisAddIn.cs#2)]  
  
 Для изменения книги при ее сохранении в приведенных выше примерах кода используются следующие объекты:  
  
-   Поле `Application` класса `ThisAddIn` . Поле `Application` возвращает объект <xref:Microsoft.Office.Interop.Excel.Application> , который представляет текущий экземпляр Excel.  
  
-   Параметр `Wb` обработчика событий для события <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> . Параметр `Wb` является объектом <xref:Microsoft.Office.Interop.Excel.Workbook> , который представляет сохраняемую книгу. Дополнительные сведения см. в разделе [обзор объектной модели Excel](../vsto/excel-object-model-overview.md).  
  
## <a name="test-the-project"></a>Тестирование проекта  
  
### <a name="to-test-the-project"></a>Тестирование проекта  
  
1.  Нажмите клавишу **F5** для построения и запуска проекта.  
  
     При построении проекта код компилируется в сборку, которая включается в выходную папку сборки для проекта. Visual Studio также создает ряд записей реестра, которые позволяют Excel обнаружить и загрузить надстройку VSTO, и настраивает параметры безопасности на компьютере разработчика, разрешая запуск надстройки VSTO. Дополнительные сведения см. в разделе [решений Office построения](../vsto/building-office-solutions.md).  
  
2.  Сохраните книгу в Excel.  
  
3.  Убедитесь, что в книгу добавляется указанный ниже текст.  
  
     **Этот текст добавляется с помощью кода.**  
  
4.  Закройте Excel.  
  
## <a name="clean-up-the-project"></a>Очистка проекта  
 Завершив разработку проекта, удалите с компьютера сборку надстройки VSTO, записи реестра и параметры безопасности. В противном случае надстройка VSTO будет запускаться при каждом открытии программы Excel на компьютере разработчика.  
  
### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Очистка завершенного проекта на компьютере разработчика  
  
1.  В Visual Studio в меню **Построение** выберите пункт **Очистить решение**.  
  
## <a name="next-steps"></a>Следующие шаги  
 Теперь, когда вы создали базовую надстройку VSTO для Excel, изучите более подробную информацию о разработке надстроек VSTO в следующих разделах.  
  
-   Общие задачи программирования, которые можно выполнять в надстройках VSTO: [программы VSTO Add-ins](../vsto/programming-vsto-add-ins.md).  
  
-   Задачи программирования, характерные для надстроек VSTO для Excel: [решения Excel](../vsto/excel-solutions.md).  
  
-   С помощью объектной модели Excel: [обзор объектной модели Excel](../vsto/excel-object-model-overview.md).  
  
-   Настройка пользовательского интерфейса (UI) из Excel, например, добавление настраиваемой вкладки на ленту или создание собственной настраиваемой области задач: [настройки пользовательского интерфейса Office](../vsto/office-ui-customization.md).  
  
-   Построение и отладка надстроек VSTO для Excel: [решений Office построения](../vsto/building-office-solutions.md).  
  
-   Развертывание надстроек VSTO для Excel: [развертывание решения Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Решения Excel](../vsto/excel-solutions.md)   
 [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)   
 [Обзор объектной модели Excel](../vsto/excel-object-model-overview.md)   
 [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)   
 [Создание решений Office](../vsto/building-office-solutions.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)   
 [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md)  
  
  