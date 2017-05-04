---
title: "Пошаговое руководство. Создание первой надстройки VSTO для Excel | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "надстройки уровня приложения [разработка решений Office в Visual Studio], создание первого проекта"
  - "разработка решений Office в Visual Studio, создание первого проекта"
  - "надстройки [разработка решений Office в Visual Studio], создание первого проекта"
  - "Excel [разработка решений Office в Visual Studio], создание первого проекта"
ms.assetid: a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Пошаговое руководство. Создание первой надстройки VSTO для Excel
  В этом вводном пошаговом руководстве показано, как создавать надстройки уровня приложения для Microsoft Office Excel. Функции, создаваемые в подобном решении, доступны для приложения независимо от того, какие книги открыты.  
  
 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   Создание проекта надстройки VSTO Excel для Excel.  
  
-   Написание кода с использованием объектной модели Excel, которая при сохранении книги добавляет в нее текст.  
  
-   Построение и запуск проекта для тестирования.  
  
-   Удаление завершенного проекта для прекращения автоматического запуска надстройки VSTO на компьютере разработчика.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Обязательные компоненты  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] или [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## Создание проекта  
  
#### Создание проекта надстройки VSTO Excel в Visual Studio  
  
1.  Запустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.  
  
3.  В области шаблонов разверните узел **Visual C\#** или **Visual Basic**, а затем узел **Office\/SharePoint**.  
  
4.  В развернутом узле **Office\/SharePoint** выберите узел **Надстройки Office**.  
  
5.  В списке шаблонов проектов выберите **Надстройку Excel 2010** или **Надстройку Excel 2013**.  
  
6.  В поле **Имя** введите **FirstExcelAddIn**.  
  
7.  Нажмите кнопку **ОК**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] создает проект **FirstExcelAddIn** и открывает файл кода ThisAddIn в редакторе.  
  
## Написание кода для добавления текста в сохраняемую книгу  
 Добавьте код в файл кода ThisAddIn. Новый код использует объектную модель Excel для вставки стандартного текста в первую строку активного листа. Активным является лист, открытый в момент сохранения книги пользователем. По умолчанию файл кода ThisAddIn содержит следующий созданный код:  
  
-   Частичное определение класса `ThisAddIn`. Этот класс предоставляет точку входа для кода и обеспечивает доступ к объектной модели Excel. Для получения дополнительной информации см. [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md). Остальная часть класса `ThisAddIn`определяется в скрытом файле кода, изменять который не следует.  
  
-   Обработчики событий `ThisAddIn_Startup` и `ThisAddIn_Shutdown`. Эти обработчики событий вызываются, когда Excel загружает и выгружает надстройку VSTO. Их можно использовать для инициализации надстройки VSTO в процессе ее загрузки, а также для освобождения используемых надбавкой ресурсов при ее выгрузке. Для получения дополнительной информации см. [События в проектах Office](../vsto/events-in-office-projects.md).  
  
#### Добавление строки текста в сохраненную книгу  
  
1.  В файл кода ThisAddIn добавьте в класс `ThisAddIn` указанный ниже код. Новый код определяет обработчик событий для события <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>, которое возникает при сохранении книги.  
  
     Когда пользователь сохраняет книгу, обработчик событий добавляет новый текст в начало активного листа.  
  
     [!code-csharp[Trin_ExcelAddInTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInTutorial/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInTutorial/VB/ThisAddIn.vb#1)]  
  
2.  Если используется C\#, добавьте в обработчик событий `ThisAddIn_Startup` указанный ниже код. Он используется для подключения обработчика событий `Application_WorkbookBeforeSave` к событию <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>.  
  
     [!code-csharp[Trin_ExcelAddInTutorial#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInTutorial/CS/ThisAddIn.cs#2)]  
  
 Для изменения книги при ее сохранении в приведенных выше примерах кода используются следующие объекты:  
  
-   Поле `Application` класса `ThisAddIn`. Поле `Application` возвращает объект <xref:Microsoft.Office.Interop.Excel.Application>, который представляет текущий экземпляр Excel.  
  
-   Параметр `Wb` обработчика событий для события <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>. Параметр `Wb` является объектом <xref:Microsoft.Office.Interop.Excel.Workbook>, который представляет сохраняемую книгу. Для получения дополнительной информации см. [Общие сведения об объектной модели Excel](../vsto/excel-object-model-overview.md).  
  
## Тестирование проекта  
  
#### Тестирование проекта  
  
1.  Нажмите клавишу **F5** для построения и запуска проекта.  
  
     При построении проекта код компилируется в сборку, которая включается в выходную папку сборки для проекта. Visual Studio также создает ряд записей реестра, которые позволяют Excel обнаружить и загрузить надстройку VSTO, и настраивает параметры безопасности на компьютере разработчика, разрешая запуск надстройки VSTO. Дополнительные сведения см. в разделе [Построение решений Office](../vsto/building-office-solutions.md).  
  
2.  Сохраните книгу в Excel.  
  
3.  Убедитесь, что в книгу добавляется указанный ниже текст.  
  
     **Этот текст добавляется с помощью кода.**  
  
4.  Закройте Excel.  
  
## Очистка проекта  
 Завершив разработку проекта, удалите с компьютера сборку надстройки VSTO, записи реестра и параметры безопасности. В противном случае надстройка VSTO будет запускаться при каждом открытии программы Excel на компьютере разработчика.  
  
#### Очистка завершенного проекта на компьютере разработчика  
  
1.  В Visual Studio в меню **Построение** выберите пункт **Очистить решение**.  
  
## Следующие действия  
 Теперь, когда вы создали базовую надстройку VSTO для Excel, изучите более подробную информацию о разработке надстроек VSTO в следующих разделах.  
  
-   Общие задачи программирования, которые можно выполнять в надстройках VSTO: [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Задачи программирования, характерные для надстроек VSTO для Excel: [Решения Excel](../vsto/excel-solutions.md).  
  
-   Использование объектной модели Excel: [Общие сведения об объектной модели Excel](../vsto/excel-object-model-overview.md)  
  
-   Настройка пользовательского интерфейса Excel, например добавление настраиваемой вкладки в ленту или создание собственной настраиваемой области задач: [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).  
  
-   Построение и отладка надстроек VSTO для Excel: [Построение решений Office](../vsto/building-office-solutions.md).  
  
-   Развертывание надстроек VSTO для Excel: [Развертывание решения Office](../vsto/deploying-an-office-solution.md).  
  
## См. также  
 [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Решения Excel](../vsto/excel-solutions.md)   
 [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md)   
 [Общие сведения об объектной модели Excel](../vsto/excel-object-model-overview.md)   
 [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)   
 [Построение решений Office](../vsto/building-office-solutions.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)   
 [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md)  
  
  